```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="计时器" />

    <Chronometer
        android:id="@+id/chronometer"
        android:text="Chronometer"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <TextView
        android:id="@+id/txt1"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"/>
</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_09;

import android.os.Bundle;
import android.os.SystemClock;
import android.widget.Chronometer;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    private Chronometer chronometer;
    private TextView txt1;
    private int Over=10,elapsedTime;

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


        chronometer = findViewById(R.id.chronometer);
        txt1 = findViewById(R.id.txt1);

        chronometer.setBase(SystemClock.elapsedRealtime());
        chronometer.setFormat("已用时间:%s");
        chronometer.start();

        chronometer.setOnChronometerTickListener(new Chronometer.OnChronometerTickListener() {
            @Override
            public void onChronometerTick(Chronometer chronometer) {
                elapsedTime = (int) ((SystemClock.elapsedRealtime() - chronometer.getBase()) / 1000);
                txt1.setText(Over - elapsedTime + "秒");
                if (elapsedTime >= Over) {
                    chronometer.stop();
                    txt1.setText("结束");
                }

            }
        });
    }

}
```

---

![image](https://github.com/user-attachments/assets/adcc6745-ae87-40e0-ba33-35f85968d9bf)
