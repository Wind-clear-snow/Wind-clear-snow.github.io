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
        android:id="@+id/tv1"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:singleLine="true"
        android:text="@string/text1"
        android:textSize="12sp"
        android:textColor="#00FF00"/>
    <TextView
        android:id="@+id/tv2"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:singleLine="true"
        android:text="@string/mutipleline"
        android:textSize="12sp"
        android:textColor="#990F80"/>
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/email"
        android:autoLink="email"
        android:height="100px"/>
    <TextView
        android:layout_width="170px"
        android:layout_height="180px"
        android:drawableTop="@drawable/icon"
        android:height="100px"
        android:textSize="10dp"
        android:text="带图片的TextView"/>
    <TextView
        android:id="@+id/tv3"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:textSize="16sp" />
    <TextView
        android:id="@+id/tv4"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:textSize="18sp" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_03;

import android.graphics.Color;
import android.os.Bundle;
import android.text.Html;
import android.text.Spannable;
import android.text.SpannableStringBuilder;
import android.text.style.ForegroundColorSpan;
import android.widget.TextView;

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

        TextView tView3 = (TextView) findViewById(R.id.tv3);
        TextView tv1 = (TextView) findViewById(R.id.tv1);

        tView3.setText(Html.fromHtml("大家好<font color='#FF0000'>改变局部颜色</font>!"));
        tv1.setText("Hello IOT ----- caixukun textview");
        String str = "根据段落改变文本颜色!物联网工程曾毅";
        TextView tView4=(TextView) findViewById(R.id.tv4);
        SpannableStringBuilder styleBuilder = new SpannableStringBuilder(str);

        styleBuilder.setSpan(new ForegroundColorSpan(Color.RED), 0, 2, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        styleBuilder.setSpan(new ForegroundColorSpan(Color.BLUE), 2, 4, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        styleBuilder.setSpan(new ForegroundColorSpan(Color.GREEN), 4, 6, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        styleBuilder.setSpan(new ForegroundColorSpan(Color.YELLOW), 6, 8, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        styleBuilder.setSpan(new ForegroundColorSpan(Color.CYAN), 8, 10, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        styleBuilder.setSpan(new ForegroundColorSpan(Color.MAGENTA), 10, 12, Spannable.SPAN_EXCLUSIVE_EXCLUSIVE);
        tView4.setText(styleBuilder);

    }
}
```

---

```cpp
<resources>
    <string name="app_name">FirstApp202_03</string>
    <string name="text1">唱跳rap</string>
    <string name="mutipleline">篮球</string>
    <string name="email">kunkun</string>

</resources>
```

---
![image](https://github.com/user-attachments/assets/d73d580d-32a2-4a1c-a67b-a6a71b11a699)
