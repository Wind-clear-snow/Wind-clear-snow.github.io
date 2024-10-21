```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="设备控制"
        android:background="#"
        android:paddingTop="10dp"
        android:paddingBottom="10dp"
        android:textAlignment="center"
        android:textColor="#FFFFFF"
        android:textSize="20sp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:paddingTop="20dp"
        android:paddingBottom="20dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp">

        <TextView
            android:id="@+id/tv1"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="@string/ventilation_system"
            android:textSize="16sp"/>

        <Spinner
            android:id="@+id/sp1"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:entries="@array/statues"/>

        <ImageView
            android:id="@+id/img1"
            android:layout_width="100px"
            android:layout_height="100px"
            android:layout_weight="1"
            android:src="@drawable/img_fan"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:paddingTop="20dp"
        android:paddingBottom="20dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp">

        <TextView
            android:id="@+id/tv2"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="@string/aircondition_system"
            android:textSize="16sp"/>

        <Spinner
            android:id="@+id/sp2"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:entries="@array/statues"/>

        <ImageView
            android:id="@+id/img2"
            android:layout_width="100px"
            android:layout_height="100px"
            android:layout_weight="1"
            android:src="@drawable/img_airconditioner_off"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:paddingTop="20dp"
        android:paddingBottom="20dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp">

        <TextView
            android:id="@+id/tv3"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="@string/lighting_system"
            android:textSize="16sp"/>

        <Spinner
            android:id="@+id/sp3"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:entries="@array/statues"/>

        <ImageView
            android:id="@+id/img3"
            android:layout_width="100px"
            android:layout_height="100px"
            android:layout_weight="1"
            android:src="@drawable/img_light_off"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:paddingTop="20dp"
        android:paddingBottom="20dp"
        android:paddingLeft="10dp"
        android:paddingRight="10dp">

        <TextView
            android:id="@+id/tv4"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:gravity="center"
            android:text="@string/cook"
            android:textSize="16sp"/>

        <Spinner
            android:id="@+id/sp4"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:entries="@array/statues"/>

        <ImageView
            android:id="@+id/img4"
            android:layout_width="100px"
            android:layout_height="100px"
            android:layout_weight="1"
            android:src="@drawable/img_cooker_off"/>

    </LinearLayout>


</LinearLayout>
```

---

```cpp
<resources>
    <string name="app_name">DeviceControl202</string>
    <string name="device_control">设备控制</string>
    <string name="ventilation_system">通风系统:</string>
    <string name="aircondition_system">空调系统:</string>
    <string name="lighting_system">照明系统:</string>
    <string name="cook">做饭系统:</string>
    <string-array name="statues">
        <item>关闭</item>
        <item>开启</item>
        <item>自动</item>
    </string-array>

</resources>
```

---

```cpp
package com.zzy.devicecontrol202;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.AdapterView;
import android.widget.AdapterView.OnItemSelectedListener;
import android.widget.ImageView;
import android.widget.Spinner;
import android.widget.TextView;
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

        Animation rotate = AnimationUtils.loadAnimation(MainActivity.this, R.anim.rotate);
        rotate.setRepeatCount(-1);

        TextView tv1 = findViewById(R.id.tv1);
        TextView tv2 = findViewById(R.id.tv2);
        TextView tv3 = findViewById(R.id.tv3);
        TextView tv4 = findViewById(R.id.tv4);

        Spinner spinner1 = findViewById(R.id.sp1);
        Spinner spinner2 = findViewById(R.id.sp2);
        Spinner spinner3 = findViewById(R.id.sp3);
        Spinner spinner4 = findViewById(R.id.sp4);

        ImageView imageView1 = findViewById(R.id.img1);
        ImageView imageView2 = findViewById(R.id.img2);
        ImageView imageView3 = findViewById(R.id.img3);
        ImageView imageView4 = findViewById(R.id.img4);


        spinner1.getSelectedItem();

        spinner1.setOnItemSelectedListener(new OnItemSelectedListener() {

            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                String result = adapterView.getItemAtPosition(i).toString();
                Toast.makeText(MainActivity.this, result + tv1.getText(), Toast.LENGTH_SHORT).show();
                imageView1.setAnimation(rotate);
                if (result.equals("开启"))
                    imageView1.startAnimation(rotate);
                else if (result.equals("关闭"))
                    imageView1.clearAnimation();
            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {
            }
        });

        spinner2.setOnItemSelectedListener(new OnItemSelectedListener() {

            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                String result = adapterView.getItemAtPosition(i).toString();
                Toast.makeText(MainActivity.this, result + tv2.getText(), Toast.LENGTH_SHORT).show();

                if (result.equals("开启"))
                    imageView2.setImageResource(R.drawable.img_airconditioner_on);
                else if (result.equals("关闭"))
                    imageView2.setImageResource(R.drawable.img_airconditioner_off);
            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {
            }
        });

        spinner3.setOnItemSelectedListener(new OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                String result = adapterView.getItemAtPosition(i).toString();
                Toast.makeText(MainActivity.this, result + tv3.getText(), Toast.LENGTH_SHORT).show();

                if (result.equals("关闭"))
                    imageView3.setImageResource(R.drawable.img_light_off);
                else if (result.equals("开启"))
                    imageView3.setImageResource(R.drawable.img_light_on);

            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {
            }
        });

        spinner4.setOnItemSelectedListener(new OnItemSelectedListener() {
            @Override
            public void onItemSelected(AdapterView<?> adapterView, View view, int i, long l) {
                String result = adapterView.getItemAtPosition(i).toString();
                Toast.makeText(MainActivity.this, result + tv4.getText(), Toast.LENGTH_SHORT).show();

                if (result.equals("关闭"))
                    imageView4.setImageResource(R.drawable.img_cooker_off);
                else if (result.equals("开启"))
                    imageView4.setImageResource(R.drawable.img_cooker_on);
            }

            @Override
            public void onNothingSelected(AdapterView<?> adapterView) {
            }
        });
    }
}
```

---

![image](https://github.com/user-attachments/assets/e053c85e-d3fe-4b98-8de8-f05c54c534f4)
