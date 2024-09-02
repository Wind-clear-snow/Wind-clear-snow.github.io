```cpp
<?xml version="1.0" encoding="utf-8"?>
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:gravity="center_vertical"
    android:stretchColumns="0,3"
    tools:context=".MainActivity">

    <TableRow android:id="@+id/TableRow01"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <TextView/>
        <TextView android:id="@+id/TextView01"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="24px"
            android:text="用户名："/>

        <EditText android:id="@+id/EditText01"
            android:textSize="24px"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入用户名"
            android:minWidth="300px"/>
        <TextView/>
    </TableRow>


    <TableRow android:id="@+id/TableRow02"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <TextView/>
        <TextView android:id="@+id/TextView02"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="24px"
            android:text="密 码："/>

        <EditText android:id="@+id/EditText02"
            android:textSize="24px"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入密码"
            android:minWidth="300px"
            android:inputType="textPassword"/>
        <TextView/>
    </TableRow>


    <TableRow android:id="@+id/TableRow03"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content">
        <TextView/>
        <TextView android:id="@+id/TextView03"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="24px"
            android:text="手机号码："/>

        <EditText android:id="@+id/EditText03"
            android:textSize="24px"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入手机号码"
            android:minWidth="300px"
            android:maxLength="11"
            android:inputType="textPhonetic"/>
        <TextView/>
    </TableRow>

    <RelativeLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="16dp">

        <Button
            android:id="@+id/Button01"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentStart="true"
            android:layout_marginStart="105dp"
            android:text="登录" />

        <Button
            android:id="@+id/Button02"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginStart="29dp"
            android:layout_toEndOf="@id/Button01"
            android:text="取消" />

    </RelativeLayout>


</TableLayout>
```