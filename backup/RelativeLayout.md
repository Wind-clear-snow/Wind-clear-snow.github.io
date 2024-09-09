```cpp
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:gravity="center_vertical"
    android:stretchColumns="0,3"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/txt"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="手机号"
        android:textSize="20dp"
        android:layout_marginBottom="5dp"
        />
    <EditText
        android:id="@+id/edit"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/txt"
        android:inputType="number"
        android:hint="请输入手机号"
        android:maxLength="11"
        android:numeric="integer"
        />

    <Button
        android:id="@+id/btn1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/edit"
        android:text="升天"
        android:layout_alignParentLeft="true"
        android:layout_marginTop="20dp"
        />

    <Button
        android:id="@+id/btn2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/edit"
        android:layout_toRightOf="@id/btn1"
        android:text="登录"
        android:layout_marginLeft="20dp"
        android:layout_marginTop="20dp"/>

</RelativeLayout>
```

---

![image](https://github.com/user-attachments/assets/14752731-d57b-4d64-9ffa-11e323a11489)
