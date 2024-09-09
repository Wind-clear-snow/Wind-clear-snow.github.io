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
    <TextView
        android:id="@+id/tv6"
        android:layout_width="40dp"
        android:layout_height="40dp"
        android:layout_gravity="center"
        android:background="#956324"
        android:text="Hello World!" />
    <ImageView
        android:src="@drawable/img"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"/>
</FrameLayout>
```
---

```cpp
package com.zzy.firstapp202_02;

import android.graphics.Color;
import android.os.Bundle;
import android.os.Handler;
import android.os.Message;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.util.Timer;
import java.util.TimerTask;

public class MainActivity extends AppCompatActivity {

    private int[] testIds = {R.id.tv1,R.id.tv2,R.id.tv3,R.id.tv4,R.id.tv5,R.id.tv6};

    private int[] colors = {Color.RED, Color.GREEN, Color.BLUE, Color.YELLOW, Color.CYAN, Color.MAGENTA};

    private TextView[] views = new TextView[testIds.length];

    private Handler handler;

    private int current = 0;

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

        for (int i = 0; i < testIds.length; i++) {
            views[i] = (TextView) findViewById(testIds[i]);
        }

        handler = new Handler(){

            public void handleMessage(Message msg) {
                if (msg.what == 0x11) {
                    for (int i = 0; i < views.length; i++) {
                        views[i].setBackgroundColor(colors[i+current % colors.length]);

                        views[i].setText("第"+i+"种颜色");
                    }

                    current = (current + 1) % colors.length;;
                }
            }
        };
        Timer timer = new Timer();

        timer.schedule(new TimerTask() {

            @Override
            public void run() {
                handler.sendEmptyMessage(0x11);
            }
        }, 0, 1000);

    }
}
```

---

![image](https://github.com/user-attachments/assets/332cfe4a-88ef-4d4c-ae0d-6ceb59b19f54)
