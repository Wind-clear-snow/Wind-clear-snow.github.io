- activity_main.xml
```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/app_name" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/myName" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/major" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/university" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/question" />

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

---
- strings.xml
```cpp
<resources>
    <string name="app_name">FirstApp202</string>
    <string name="myName">Wind-clear-snow</string>
    <string name="major">IOT</string>
    <string name="university">wind</string>
    <string name="question">你叫什么名字？</string>
    <string name="true_button">true</string>
    <string name="false_button">false</string>
</resources>
```

---
-效果
![image](https://github.com/user-attachments/assets/c73f747b-67a8-4d64-8e8c-7a1ad530668f)
