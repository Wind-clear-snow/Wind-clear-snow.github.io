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
        android:text="SetAction打开其他应用" />

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn1"
            android:layout_width="120dp"
            android:layout_height="40dp"
            android:text="拨打电话"/>

        <EditText
            android:id="@+id/et1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入电话号码" />

    </LinearLayout>

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn2"
            android:layout_width="120dp"
            android:layout_height="40dp"
            android:text="发送短信" />

        <EditText
            android:id="@+id/et2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入短信内容" />

    </LinearLayout>

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn3"
            android:layout_width="120dp"
            android:layout_height="40dp"
            android:text="打开网页" />

        <EditText
            android:id="@+id/et3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="请输入网址" />

    </LinearLayout>


</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_15;

import android.Manifest;
import android.content.Intent;
import android.content.pm.PackageManager;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Switch;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.content.ContextCompat;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.core.app.ActivityCompat;

public class MainActivity extends AppCompatActivity {

    public EditText et1, et2, et3;

    private static final int PERMISSION_REQUEST_CALL_PHONE = 1;

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

        et1 = findViewById(R.id.et1);
        et2 = findViewById(R.id.et2);
        et3 = findViewById(R.id.et3);

        Button btn1 = findViewById(R.id.btn1);
        btn1.setOnClickListener(clickListener);

        Button btn2 = findViewById(R.id.btn2);
        btn2.setOnClickListener(clickListener);

        Button btn3 = findViewById(R.id.btn3);
        btn3.setOnClickListener(clickListener);

        if (ContextCompat.checkSelfPermission(this, Manifest.permission.CALL_PHONE)!= PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.CALL_PHONE}, PERMISSION_REQUEST_CALL_PHONE);
        }
    }

    private View.OnClickListener clickListener = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent intent = new Intent();
            Button btn = (Button) v;
            int id = btn.getId();
            if (id == R.id.btn1) {
                if (ContextCompat.checkSelfPermission(MainActivity.this, Manifest.permission.CALL_PHONE) == PackageManager.PERMISSION_GRANTED) {
                    intent.setAction(Intent.ACTION_CALL);
                    intent.setData(Uri.parse("tel:" + et1.getText().toString()));
                    startActivity(intent);
                } else {
                    Toast.makeText(MainActivity.this, "需要授予拨打电话权限才能进行此操作", Toast.LENGTH_SHORT).show();
                }
            } else if (id == R.id.btn2) {
                intent.setAction(Intent.ACTION_SENDTO);
                intent.setData(Uri.parse("smsto:" + et1.getText().toString()));
                intent.putExtra("sms_body",et2.getText().toString());
                startActivity(intent);
            } else if (id == R.id.btn3) {
                intent.setAction(Intent.ACTION_VIEW);
                intent.setData(Uri.parse("https://" + et3.getText().toString()));
                startActivity(intent);
            }
        }
    };

    // 处理权限请求的结果
    @Override
    public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        if (requestCode == PERMISSION_REQUEST_CALL_PHONE) {
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                if (clickListener!= null && findViewById(R.id.btn1)!= null) {
                    Button btn1 = findViewById(R.id.btn1);
                    btn1.performClick();
                }
            } else {
                Toast.makeText(this, "您拒绝了拨打电话权限，无法进行此操作", Toast.LENGTH_SHORT).show();
            }
        }
    }
}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.telephony"
        android:required="false" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.FirstApp202_15"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

    <uses-permission android:name="android.permission.CALL_PHONE"/>
    <uses-permission android:name="android.permission.SEND_SMS"/>
    <uses-permission android:name="android.permission.INTERNET"/>

</manifest>
```

---

![image](https://github.com/user-attachments/assets/bdb8ef3a-6fed-4632-8bc5-24abef47c5f0)
