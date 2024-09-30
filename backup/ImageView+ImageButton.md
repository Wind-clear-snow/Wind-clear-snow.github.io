```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="5px"
        android:layout_weight="1"
        android:adjustViewBounds="true"
        android:maxHeight="200px"
        android:maxWidth="300px"
        android:scaleType="center"
        android:src="@drawable/a01"
        android:background="@drawable/a02"
        android:tint="#99FF0000"
        tools:ignore="UseAppTint" />
    <ImageButton
        android:id="@+id/imageButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:src="@drawable/a03"
        android:background="#000" />
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="变换图片" />

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="变换图片(kunkun)" />
</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_07;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.ImageButton;
import android.widget.ImageView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    ImageView img;
    int count = 0;
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

        Button btn = findViewById(R.id.button);
        ImageButton btn2 = findViewById(R.id.imageButton);
        Button btn3 = findViewById(R.id.button1);

        img = findViewById(R.id.imageView);
        btn.setOnClickListener(v -> {
            img.setBackgroundResource(R.drawable.a03);
            img.setImageResource(R.drawable.a04);
            Toast.makeText(this, "更换成功", Toast.LENGTH_SHORT).show();
        });

        btn2.setOnClickListener(v -> {
           img.setBackgroundResource(R.drawable.a01);
           img.setImageResource(R.drawable.a02);
           Toast.makeText(this, "更换成功", Toast.LENGTH_SHORT).show();
        });

        btn3.setOnClickListener(v -> {
            count++;
            btn2.setImageResource(R.drawable.ikunbtn);
            if (count % 2 == 0) {
                img.setBackgroundResource(R.drawable.ikun3);
                img.setImageResource(R.drawable.ikun4);
            } else {
                img.setBackgroundResource(R.drawable.ikun1);
                img.setImageResource(R.drawable.ikun2);
            }
        });
    }
}
```

---

![image](https://github.com/user-attachments/assets/d2d4e0ae-2473-40e7-881d-44ed647e964b)
