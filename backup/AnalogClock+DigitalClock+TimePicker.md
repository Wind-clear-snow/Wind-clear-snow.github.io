```cpp
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">
    <RelativeLayout
        android:layout_width="fill_parent"
        android:layout_height="fill_parent">

        <TextView
            android:id="@+id/tv"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:textSize="20dp"
            android:textColor="#00ff00"
            android:text="AnalogClock应用" />

        <AnalogClock
            android:id="@+id/analogClock"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@+id/tv"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="30dp"
            android:layerType="software" />

        <TextView
            android:id="@+id/tv2"
            android:layout_width="fill_parent"
            android:layout_height="wrap_content"
            android:layout_below="@+id/analogClock"
            android:textSize="20dp"
            android:textColor="#00ff00"
            android:text="DigitalClock应用" />

        <DigitalClock
            android:id="@+id/digitalClock"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@+id/tv2"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="32dp"
            android:text="DigitalClock"
            android:textSize="30dp"
            android:textColor="#ff0000" />

        <TimePicker
            android:id="@+id/timepicker"
            android:layout_width="300dp"
            android:layout_height="340dp"
            android:layout_below="@+id/digitalClock"
            android:timePickerMode="clock"
            android:background="#ffffffff" />

    </RelativeLayout>

</ScrollView>
```

---

![image](https://github.com/user-attachments/assets/7834cf97-5fe4-48fe-a3d2-0bfafc1b451c)
