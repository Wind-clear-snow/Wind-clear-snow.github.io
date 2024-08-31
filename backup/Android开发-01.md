### Android开发-01
首先安装Android Studio 安装不做讲述
安装完界面
![image](https://github.com/user-attachments/assets/415b0126-38af-444d-a652-acf1d42fbfaa)

---
1. 开始创建第一个项目
点击New Project
![image](https://github.com/user-attachments/assets/efbe8613-5b2b-41f0-91c4-6bc620139193)

这里选择Phone and Tablet 里的Empty Views Activity ~~注:这里不选择Empty Activity 这个的默认语言为Kotlin本次使用将以Java为主要语言~~
![image](https://github.com/user-attachments/assets/af7b647e-4ccd-40e0-b1e2-8a61d3655fb6)

- Name自己定义 
- Package name ~~遵守DNS反转约定~~ com.zzy.myapplication 
- Save localtin 按自己喜好选择
- Language 这里选择java
- MInimum SDK 默认
- Build configuration language 默认
选择完点击Finsh等待加载完成 [若加载速度慢则参照](https://blog.csdn.net/moresi/article/details/136206437)

![image](https://github.com/user-attachments/assets/b55a31a2-cdd0-4883-a524-a5245e14f350)

这是加载完成的项目结构 创建完会自动打开MainActivity activity_main.xml

![image](https://github.com/user-attachments/assets/2b5f0ca6-58cb-43ae-993b-b0bb409894e7)

2.  activity_main.xml介绍

这是activity_main.xml的初始样子 根据版本的不同初始的也不一样 ~~都大差不差的~~

![image](https://github.com/user-attachments/assets/7d727a2a-1b4f-456f-9bdc-12ee796421ea)

可以点击右上角来切换Text和Design

![image](https://github.com/user-attachments/assets/55656a23-161e-44ca-867f-3d2bdab00a73)

布局文件的命名基于其关联的activity：activity_为前缀,activity子类名的其余部分全转为小写的在其后
例如: MainActivity 的布局文件名为activity_main

3. activity的布局定义

默认布局有ConstraintLayout TextView这两个视图 用户能交互的视图为部件

![image](https://github.com/user-attachments/assets/8c1170dd-9b3a-4cbd-b68d-c5b5456a9e82)

上图中的默认部件不是我们需要的
- 一个垂直的LinearLayout
- 一个TextView部件
- 一个水平的LinearLayout
- 两个Button部件
activity_main.xml代码如下
```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/question_text" />

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:layout_height="wrap_content"
            android:layout_width="wrap_content"
            android:text="@string/true_button"/>

        <Button
            android:layout_height="wrap_content"
            android:layout_width="wrap_content"
            android:text="@string/false_button"/>

    </LinearLayout>

</LinearLayout>
```
strings.xml的代码如下
```cpp
<resources>
    <string name="app_name">My Application</string>
    <string name="question_text">how are you</string>
    <string name="true_button">true</string>
    <string name="false_button">false</string>

</resources>
```
效果为

![image](https://github.com/user-attachments/assets/f76b849d-cf25-4d9d-8d46-63a56466eb5d)

4. 部件属性
 1. android:layout_width和android:layout_height
  几乎所有部件都需要的属性 以下是常见的属性值
 - match_parent：视图与其父视图大小相同
 - wrap_content：视图将根据其显示内容自动调整大小
 例:
  ```cpp
<TextView
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:text="@string/question_text" />
 ```
 2. android:orientation
  这个属性决定部件是水平放置还是垂直放置 属性值为
  - vertical 垂直
  - horizontal 水平
 ```cpp
     <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">
    </LinearLayout>
    
    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical">
    </LinearLayout>
 ```
 
 3. android:text
 该属性指定部件显示的文字 注意:该属性的值不为字符串 而是以@string/语法形式对字符串资源(strings.xml)的引用
 ```cpp
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/question_text" />
 ```