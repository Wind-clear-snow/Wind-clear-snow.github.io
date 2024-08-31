- activity_main.xml
```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="fill_parent"
        android:orientation="horizontal"
        android:layout_weight="1">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="fill_parent"
            android:text="红色"
            android:gravity="center"
            android:background="#FF0000"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="fill_parent"
            android:text="蓝色"
            android:textColor="@color/white"
            android:gravity="bottom"
            android:background="#0000FF"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="fill_parent"
            android:text="黄色"
            android:gravity="top|center"
            android:background="#FFFF00"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="fill_parent"
            android:text="绿色"
            android:layout_gravity="center"
            android:gravity="fill_vertical"
            android:background="#00FF00"
            android:layout_weight="1"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="fill_parent"
        android:orientation="vertical"
        android:layout_weight="1">

        <TextView
            android:layout_width="fill_parent"
            android:layout_height="fill_parent"
            android:text="第一"
            android:gravity="center"
            android:background="#FF00FF"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="300dp"
            android:layout_height="fill_parent"
            android:text="第二"
            android:gravity="center"
            android:background="#FFA500"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="200dp"
            android:layout_height="fill_parent"
            android:text="第三"
            android:gravity="center"
            android:background="#808080"
            android:layout_weight="1"/>

        <TextView
            android:layout_width="100dp"
            android:layout_height="fill_parent"
            android:text="第四"
            android:gravity="center"
            android:background="#C0C0C0"
            android:layout_weight="1"/>

    </LinearLayout>

</LinearLayout>
```

---
- 效果
![image](https://github.com/user-attachments/assets/96b07c05-c998-4597-ab9c-384780d0ad03)
