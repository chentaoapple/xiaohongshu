#### view树的绘制流程

- ###### OnMeasure()：

  测量视图大小。从顶层父View到子View递归调用measure方法，measure方法又回调OnMeasure。

- ###### OnLayout()：

  确定View位置，进行页面布局。从顶层父View向子View的递归调用view.layout方法的过程，即父View根据上一步measure子View所得到的布局大小和布局参数，将子View放在合适的位置上。

- ###### OnDraw()：

  绘制视图。ViewRoot创建一个Canvas对象，然后调用OnDraw()。六个步骤：①、绘制视图的背景；②、保存画布的图层（Layer）；③、绘制View的内容；④、绘制View子视图，如果没有就不用；⑤、还原图层（Layer）；⑥、绘制滚动条。

  

onMeasure:

MeasureSpec 32位的int值 前两位代表模式 后30位测量规格的大小

###### 3种模式

UNSPECIFIED：不对View大小做限制，如：ListView，ScrollView
 EXACTLY：确切的大小，如：100dp或者march_parent
 AT_MOST：大小不可超过某数值，如：wrap_content



###### 子View的MeasureSpec

子View的MeasureSpec由父View的MeasureSpec和子View本身的LayoutPramas共同决定，在ViewGroup的getChildMeasureSpec方法中实现

不管父View是何模式，若子View有确切数值，则子View大小就是其本身大小，且mode是EXACTLY
 若子View是match_parent，则模式与父View相同，且大小同父View（若父View是UNSPECIFIED，则子View大小为0）
 若子View是wrap_content，则模式是AT_MOST，大小同父View，表示不可超过父View大小（若父View是UNSPECIFIED，则子View大小为0）



onlayout:

ViewGroup控件中，onLayout配合onMeasure方法一起使用可以实现自定义View的复杂布局。自定义View首先调用onMeasure进行测量，然后调用onLayout方法动态获取子View和子View的测量大小，然后进行layout布局。

getWidth()、getHeight()和getMeasuredWidth()、getMeasuredHeight()这两对方法之间的区别（上面分析measure过程已经说过getMeasuredWidth()、getMeasuredHeight()必须在onMeasure之后使用才有效）。可以看出来getWidth()与getHeight()方法必须在layout(int l, int t, int r, int b)执行之后才有效。



draw:

invalidate()请求android系统 如果大小没有发生变化 就不会调用layout放置这个过程

requestLayout() 当布局发生变化时 希望重新测量尺寸大小 就会触发 measure和layout 但不会调用draw方法







