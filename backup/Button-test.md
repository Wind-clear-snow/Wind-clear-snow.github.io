```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="fill_parent"
        android:layout_height="match_parent"
        android:text="按钮事件" />

    <Button
        android:id="@+id/btn1"
        android:layout_width="120dp"
        android:layout_height="wrap_content"
        android:text="按钮一" />

    <Button
        android:id="@+id/btn2"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="按钮二" />
    <Button
        android:id="@+id/btn3"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="按钮三" />
    <Button
        android:id="@+id/btn4"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="按钮四" />

</LinearLayout>
```

---

```cpp
package com.zzy.firshtapp202_04;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import android.view.View.OnClickListener;

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

        Button btn1 = (Button)findViewById(R.id.btn1);
        Button btn2 = (Button)findViewById(R.id.btn2);
        Button btn3 = (Button)findViewById(R.id.btn3);
        Button btn4 = (Button)findViewById(R.id.btn4);

        btn1.setOnClickListener(listener);
        btn2.setOnClickListener(listener);
        btn3.setOnClickListener(listener);
        btn4.setOnClickListener(listener);

    }

    private OnClickListener listener = new OnClickListener() {

        @Override
        public void onClick(View view) {
            Button btn = (Button)view;
            switch (btn.getId()){
                case R.id.btn1:
                    Toast.makeText(MainActivity.this, "按钮一事件",Toast.LENGTH_LONG).show();
                    break;
                case R.id.btn2:
                    Toast.makeText(MainActivity.this, "按钮二事件",Toast.LENGTH_SHORT).show();
                    break;
                case R.id.btn3:
                    Toast.makeText(MainActivity.this, "按钮三事件",Toast.LENGTH_SHORT).show();
                    break;
                case R.id.btn4:
                    Toast.makeText(MainActivity.this, "按钮四事件",Toast.LENGTH_SHORT).show();
                    break;
            }
        }
    };
}
```

---

![image](https://github.com/user-attachments/assets/72d7a54f-c7c2-48ce-b665-7b8dbdc9e3c9)
