### LayoutInflater--布局解析器

将XML布局文件实例化对应View对象，

```java
Activity.getLayoutInflater()

Context.getSystemService() 
 
final View content = LayoutInflater.from(this).inflate(R.layout.content, root, false);
```



##### LayoutInflater创建过程

两种创建方式

```java
final LayoutInflater getLayoutInflater = getLayoutInflater();
final LayoutInflater getSystemServiceInflater = (LayoutInflater) getSystemService(Context.LAYOUT_INFLATER_SERVICE);
```

**每个 Activity 都有其独一无二的 LayoutInflater，它的实际类型是 PhoneLayoutInflater**



