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
        android:text="欢迎参与问卷调查"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_marginTop="20dp"
        android:layout_marginBottom="20dp" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="性别:" />

    <RadioGroup
        android:id="@+id/sex"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <RadioButton
            android:id="@+id/man"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="男"
            android:checked="true"/>

        <RadioButton
            android:id="@+id/woman"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="女"/>

    </RadioGroup>


    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="您的职业是：" />

    <EditText
        android:id="@+id/occupationEditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

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
package com.zzy.firstapp202_05;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.RadioGroup.OnCheckedChangeListener;
import android.widget.Spinner;
import android.view.View.OnClickListener;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;



public class MainActivity extends AppCompatActivity {

    private RadioGroup sexRadioGroup;
    private EditText occupationEditText;
    private Button submitButton;

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

        sexRadioGroup = findViewById(R.id.sex);
        occupationEditText = findViewById(R.id.occupationEditText);
        submitButton = findViewById(R.id.submit);

        // 设置提交按钮的点击事件监听器
        submitButton.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View v) {
                String gender = ((RadioButton) findViewById(sexRadioGroup.getCheckedRadioButtonId())).getText().toString();
                String occupation = occupationEditText.getText().toString();

                // 在这里可以对收集到的问卷数据进行处理，比如打印输出或存储到数据库等
                Log.i("gender","性别：" + gender);
                Log.i("occupation","职业：" + occupation);

                Toast.makeText(MainActivity.this, "性别：" + gender + "，职业：" + occupation, Toast.LENGTH_SHORT).show();
            }
        });

        sexRadioGroup.setOnCheckedChangeListener(new OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup group, int checkedId) {
                // 在这里可以对性别选项的变化进行处理，比如显示或隐藏某些控件等
                RadioButton selectedRadioButton = findViewById(checkedId);
                Log.i("MainActivity", "Selected gender: " + selectedRadioButton.getText());
                Toast.makeText(MainActivity.this, "Selected gender: " + selectedRadioButton.getText(), Toast.LENGTH_SHORT).show();
            }
        });



    }

}
```

---

![image](https://github.com/user-attachments/assets/95ab3d94-f4b5-46ff-aa4c-aa02da18182f)
