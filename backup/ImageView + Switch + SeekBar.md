```cpp
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv_header"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_marginStart="0dp"
        android:layout_marginTop="10dp"
        android:layout_marginBottom="10dp"
        android:gravity="center"
        android:textSize="24sp"
        android:text="City Light" />

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_alignParentStart="true"
        android:layout_centerVertical="true"
        android:layout_below="@+id/tv_header"
        android:orientation="horizontal"
        android:layout_marginRight="0dp">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:id="@+id/tv1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="街区1"/>

            <ImageView
                android:id="@+id/iv1"
                android:layout_width="110dp"
                android:layout_height="160dp"
                android:scaleType="fitXY"
                android:src="@drawable/img1"/>

            <Switch
                android:id="@+id/sw1"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text=""/>

            <SeekBar
                android:id="@+id/sb1"
                android:layout_width="110dp"
                android:layout_height="wrap_content"/>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:id="@+id/tv2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="街区2"/>

            <ImageView
                android:id="@+id/iv2"
                android:layout_width="110dp"
                android:layout_height="160dp"
                android:scaleType="fitXY"
                android:src="@drawable/img2"/>

            <Switch
                android:id="@+id/sw2"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text=""/>

            <SeekBar
                android:id="@+id/sb2"
                android:layout_width="110dp"
                android:layout_height="wrap_content"/>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:orientation="vertical">

            <TextView
                android:id="@+id/tv3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="街区3"/>

            <ImageView
                android:id="@+id/iv3"
                android:layout_width="110dp"
                android:layout_height="160dp"
                android:scaleType="fitXY"
                android:src="@drawable/img3"/>

            <Switch
                android:id="@+id/sw3"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text=""/>

            <SeekBar
                android:id="@+id/sb3"
                android:layout_width="110dp"
                android:layout_height="wrap_content"/>

        </LinearLayout>




    </LinearLayout>

</RelativeLayout>
```

---

```cpp
package com.zzy.firstapp202_23;

import android.os.Bundle;
import android.widget.CompoundButton;
import android.widget.ImageView;
import android.widget.SeekBar;
import android.widget.Switch;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

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


        init(findViewById(R.id.iv1), findViewById(R.id.sw1), findViewById(R.id.sb1), 1);


        init(findViewById(R.id.iv2), findViewById(R.id.sw2), findViewById(R.id.sb2), 2);


        init(findViewById(R.id.iv3), findViewById(R.id.sw3), findViewById(R.id.sb3), 3);
    }

    private void init(final ImageView iv, final Switch sw, final SeekBar sb, final int switchId) {
        iv.setAlpha(1.0f);
        sw.setChecked(true);
        sb.setProgress(100);


        sw.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton compoundButton, boolean b) {
                if (b) {
                    switch (switchId) {
                        case 1:
                            iv.setAlpha(1.0f);
                            Toast.makeText(MainActivity.this, "街区 1 灯光 已打开", Toast.LENGTH_SHORT).show();
                            break;
                        case 2:
                            iv.setAlpha(1.0f);
                            Toast.makeText(MainActivity.this, "街区 2 灯光 已打开", Toast.LENGTH_SHORT).show();
                            break;
                        case 3:
                            iv.setAlpha(1.0f);
                            Toast.makeText(MainActivity.this, "街区 3 灯光 已打开", Toast.LENGTH_SHORT).show();
                            break;
                    }
                } else {
                    switch (switchId) {
                        case 1:
                            iv.setAlpha(0.2f);
                            Toast.makeText(MainActivity.this, "街区 1 灯光 已关闭", Toast.LENGTH_SHORT).show();
                            break;
                        case 2:
                            iv.setAlpha(0.2f);
                            Toast.makeText(MainActivity.this, "街区 2 灯光 已关闭", Toast.LENGTH_SHORT).show();
                            break;
                        case 3:
                            iv.setAlpha(0.2f);
                            Toast.makeText(MainActivity.this, "街区 3 灯光 已关闭", Toast.LENGTH_SHORT).show();
                            break;
                    }
                }
            }
        });


        sb.setOnSeekBarChangeListener(new SeekBar.OnSeekBarChangeListener() {
            @Override
            public void onProgressChanged(SeekBar seekBar, int i, boolean b) {

                float alpha = (float) (i * 0.008 + 0.2);
                iv.setAlpha(alpha);
                Toast.makeText(MainActivity.this, "进度：" + i, Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onStartTrackingTouch(SeekBar seekBar) {
                Toast.makeText(MainActivity.this, "开始拖动", Toast.LENGTH_SHORT).show();
            }

            @Override
            public void onStopTrackingTouch(SeekBar seekBar) {
                Toast.makeText(MainActivity.this, "停止拖动", Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

---

![image](https://github.com/user-attachments/assets/a3057828-9a98-4452-ba31-e8537b215bd0)
