```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/btn1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send SMS Broadcast" />

    <Button
        android:id="@+id/btn2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send Boradcast for Battery" />


</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_21;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.content.IntentFilter;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.localbroadcastmanager.content.LocalBroadcastManager;

public class MainActivity extends AppCompatActivity {
    private static final String action = "android.provider.Telephony.SMS_RECEIVED";

    private IntentFilter intentFilter;
    private SMSReceiver SMSReceiver;
    private LocalBroadcastManager localBroadcastManager;

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

        localBroadcastManager = LocalBroadcastManager.getInstance(this);
        Button btn1 = findViewById(R.id.btn1);
        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent = new Intent(action);
                localBroadcastManager.sendBroadcast(intent);
            }

        });

        intentFilter = new IntentFilter();
        intentFilter.addAction(action);

        SMSReceiver = new SMSReceiver();
        localBroadcastManager.registerReceiver(SMSReceiver, intentFilter);
        Button btn2 = findViewById(R.id.btn2);
        btn2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
               registerReceiver(new BatteryReceiver(), new IntentFilter(Intent.ACTION_BATTERY_CHANGED));
            }

        });

    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        localBroadcastManager.unregisterReceiver(SMSReceiver);
    }

    class LocalReceiver extends BroadcastReceiver {
        @Override
        public void onReceive(Context context, Intent intent) {

            Toast.makeText(context, "received my local broadcast", Toast.LENGTH_SHORT).show();
            Log.i("TAG", "onReceive: received my local broadcast");
        }
    }
}
```

---

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-feature
        android:name="android.hardware.telephony"
        android:required="true" />

    <uses-permission android:name="android.permission.RECEIVE_SMS" />

    <uses-permission android:name="android.permission.READ_SMS" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.FirstApp202_21"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <receiver android:name=".BatteryReceiver"
            android:enabled="true"
            android:exported="true"/>
        <receiver android:name=".SMSReceiver"
            android:exported="true"
            android:enabled="true"
            android:permission="android.permission.BROADCAST_SMS">
            <intent-filter>
                <action android:name="android.provider.Telephony.SMS_RECEIVED" />
                <action android:name="android.provider.Telephony.SMS_DELIVER" />
            </intent-filter>
        </receiver>
    </application>

</manifest>
```

---

```cpp
package com.zzy.firstapp202_21;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.util.Log;
import android.widget.Toast;

public class BatteryReceiver extends BroadcastReceiver {
    @Override
    public void onReceive(Context context, Intent intent) {
        String action = intent.getAction();
        if (Intent.ACTION_BATTERY_CHANGED.equals(action)) {
            // 获取电池电量
            int level = intent.getIntExtra("level", 0);
            // 获取电池总电量
            int scale = intent.getIntExtra("scale", 100);
            // 计算电池电量百分比
            int batteryPct = level * 100 / scale;
            Toast.makeText(context, "当前电量：" + batteryPct + "%", Toast.LENGTH_SHORT).show();
            Log.i("TAG", "当前电量：" + batteryPct + "%");

            //低电量警告
            if (batteryPct <= 20) {
                Toast.makeText(context, "电量不足，请充电", Toast.LENGTH_SHORT).show();
                Log.i("TAG", "电量不足，请充电");
            }
        }
    }
}
```

---

```cpp
package com.zzy.firstapp202_21;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.util.Log;
import android.widget.Toast;

public class SMSReceiver extends BroadcastReceiver {
    public SMSReceiver() {}

    private static final String action = "android.provider.Telephony.SMS_RECEIVED";

    @Override
    public void onReceive(Context context, Intent intent) {
        String action1 = intent.getAction();
        if (action.equals(action1)) {
            Toast.makeText(context, "收到新短信", Toast.LENGTH_SHORT).show();
            Log.d("TAG", "收到新短信");
        }
    }
}
```

---
![image](https://github.com/user-attachments/assets/9108dfde-6a1b-4c59-8f76-83bd0ce23f21)


