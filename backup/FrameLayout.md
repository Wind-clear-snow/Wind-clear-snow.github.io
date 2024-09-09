```cpp
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv1"
        android:layout_width="240dp"
        android:layout_height="240dp"
        android:layout_gravity="center"
        android:background="#134568"
        android:text="Hello World!" />

    <TextView
        android:id="@+id/tv2"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_gravity="center"
        android:background="#965412"
        android:text="Hello World!" />
    <TextView
        android:id="@+id/tv3"
        android:layout_width="160dp"
        android:layout_height="160dp"
        android:layout_gravity="center"
        android:background="#789159"
        android:text="Hello World!" />
    <TextView
        android:id="@+id/tv4"
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:layout_gravity="center"
        android:background="#465197"
        android:text="Hello World!" />
    <TextView
        android:id="@+id/tv5"
        android:layout_width="80dp"
        android:layout_height="80dp"
        android:layout_gravity="center"
        android:background="#786549"
        android:text="Hello World!" />

</FrameLayout>
```
---

```cpp
package com.zzy.firstapp202_01;

import android.annotation.SuppressLint;
import android.graphics.Color;
import android.os.Bundle;
import android.os.Handler;
import android.os.Message;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.util.Timer;
import java.util.TimerTask;

public class MainActivity extends AppCompatActivity {

    TextView t1,t2,t3,t4,t5;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        t1=(TextView) findViewById(R.id.tv1);
        t2=(TextView) findViewById(R.id.tv2);
        t3=(TextView) findViewById(R.id.tv3);
        t4=(TextView) findViewById(R.id.tv4);
        t5=(TextView) findViewById(R.id.tv5);


        t1.setText("hello");
        t1.setTextColor(getResources().getColor(R.color.black));
        t2.setText("world");
        t2.setTextColor(getResources().getColor(R.color.white));
        t3.setText("zzy");
        t3.setTextColor(getResources().getColor(R.color.colorAccent));
        t4.setText("IOT");
        t4.setTextColor(getResources().getColor(R.color.colorPrimaryDark));
        t5.setText("test");
        t5.setTextColor(getResources().getColor(R.color.colorPrimaryDark));



    }
}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="colorPrimaryLight">#B3E5FC</color>
    <color name="colorPrimaryDarkLight">#81D4FA</color>
    <color name="colorAccentLight">#80D8FF</color>
    <color name="colorPrimaryDarkLighter">#4FC3F7</color>
    <color name="colorPrimaryLighter">#B3E5FC</color>
    <color name="colorAccentLighter">#80D8FF</color>
</resources>
```

![image](https://github.com/user-attachments/assets/f18bd50f-993f-408a-b892-2690a13a6192)
