```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/num1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="输入第一个数字"
        android:inputType="numberDecimal" />

    <EditText
        android:id="@+id/num2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="输入第二个数字"
        android:inputType="numberDecimal" />

    <Button
        android:id="@+id/btn1"
        android:layout_width="120dp"
        android:layout_height="wrap_content"
        android:text="加(+)" />

    <Button
        android:id="@+id/btn2"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="减(-)" />
    <Button
        android:id="@+id/btn3"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="乘(*)" />
    <Button
        android:id="@+id/btn4"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="除(÷)" />
    <Button
        android:id="@+id/btn5"
        android:layout_width="240px"
        android:layout_height="wrap_content"
        android:text="乘方" />

    <TextView
        android:id="@+id/result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="18sp"
        android:text="结果：" />

</LinearLayout>
```

---

```cpp
package com.zzy.firshtapp202_04;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import android.view.View.OnClickListener;

public class MainActivity extends AppCompatActivity {

    private EditText num1EditText, num2EditText;
    private TextView resultTextView;

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

        num1EditText = findViewById(R.id.num1);
        num2EditText = findViewById(R.id.num2);
        resultTextView = (TextView)findViewById(R.id.result);

        Button btn1 = (Button)findViewById(R.id.btn1);
        Button btn2 = (Button)findViewById(R.id.btn2);
        Button btn3 = (Button)findViewById(R.id.btn3);
        Button btn4 = (Button)findViewById(R.id.btn4);
        Button btn5 = (Button)findViewById(R.id.btn5);


        btn1.setOnClickListener(listener);
        btn2.setOnClickListener(listener);
        btn3.setOnClickListener(listener);
        btn4.setOnClickListener(listener);
        btn5.setOnClickListener(listener);

    }

    private OnClickListener listener = new OnClickListener() {

        @Override
        public void onClick(View v) {
            String num1Str = num1EditText.getText().toString();
            String num2Str = num2EditText.getText().toString();

            if (num1Str.isEmpty() || num2Str.isEmpty()) {
                Toast.makeText(MainActivity.this, "请输入两个数字", Toast.LENGTH_SHORT).show();
                return;
            }

            double num1 = Double.parseDouble(num1Str);
            double num2 = Double.parseDouble(num2Str);
            double result = 0;
            String operation = "";

            switch (v.getId()) {
                case R.id.btn1:
                    result = num1 + num2;
                    operation = "加";
                    break;
                case R.id.btn2:
                    result = num1 - num2;
                    operation = "减";
                    break;
                case R.id.btn3:
                    result = num1 * num2;
                    operation = "乘";
                    break;
                case R.id.btn4:
                    if (num2 != 0) {
                        result = num1 / num2;
                        operation = "除";
                    } else {
                        Toast.makeText(MainActivity.this, "除数不能为零", Toast.LENGTH_SHORT).show();
                        return;
                    }
                    break;
                case R.id.btn5:
                    result = Math.pow(num1, num2);
                    operation = "乘方";
                    break;
            }
            Toast.makeText(MainActivity.this, "结果 (" + operation + ")：" + result,Toast.LENGTH_SHORT).show();
            resultTextView.setText("结果 (" + operation + ")：" + result);
        }
    };
}
```

---

![image](https://github.com/user-attachments/assets/e2609b13-9317-45ea-ac60-a9433999b2c6)
