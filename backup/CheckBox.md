```cpp
<?xml version="1.0" encoding="UTF-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="您的兴趣爱好：" />

    <CheckBox
        android:id="@+id/cb1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="阅读" />

    <CheckBox
        android:id="@+id/cb2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="音乐" />

    <CheckBox
        android:id="@+id/cb3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="运动" />

    <CheckBox
        android:id="@+id/cb4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="篮球" />

    <CheckBox
        android:id="@+id/cb5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="足球" />

    <CheckBox
        android:id="@+id/cb6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="游泳" />


    <Button
        android:id="@+id/submit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="提交"
        android:layout_marginTop="20dp" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_06;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.CheckBox;
import android.view.View.OnClickListener;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;

import android.widget.RadioGroup.OnCheckedChangeListener;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private int[] testIds = {R.id.cb1, R.id.cb2, R.id.cb3, R.id.cb4, R.id.cb5, R.id.cb6};
    private CheckBox[] cb = new CheckBox[testIds.length];

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
            cb[i] = (CheckBox) findViewById(testIds[i]);
        }

        for (int i = 0; i < testIds.length; i++) {
            cb[i].setOnCheckedChangeListener((buttonView, isChecked) -> {
                if (isChecked) {
                    Log.i("CheckBox", "选中了复选框：" + buttonView.getText());
                    Toast.makeText(MainActivity.this, "选中了复选框：" + buttonView.getText(), Toast.LENGTH_SHORT).show();
                }
            });
        }

        final Button sub = (Button) findViewById(R.id.submit);

        sub.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View view) {
                StringBuilder interests = new StringBuilder();
                for (CheckBox checkBox : cb) {
                    if (checkBox.isChecked()) {
                        interests.append(checkBox.getText()).append(", ");
                    }
                }
                if (interests.length() > 0) {
                    interests.setLength(interests.length() - 2);
                }
                Log.i("checkBoxes", "勾选了: " + interests);
                Toast.makeText(MainActivity.this, "勾选了: " + interests, Toast.LENGTH_SHORT).show();
            }
        });


    }

}
```

---

![image](https://github.com/user-attachments/assets/130aa770-438b-4a6a-9840-cca5422bb91e)

