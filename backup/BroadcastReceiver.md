```cpp
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/text_header"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginBottom="3dp"
        android:layout_marginTop="3dp"
        android:gravity="center"
        android:text="FireAlarmSystem"
        android:textSize="18sp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_below="@+id/text_header"
        android:layout_marginLeft="12dp"
        android:orientation="vertical"
        android:layout_gravity="center">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/img1"
                android:layout_width="200dp"
                android:layout_height="100dp"
                android:layout_marginTop="1dp"
                android:scaleType="fitXY"
                android:src="@color/black"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center"
                android:orientation="vertical">

                <Button
                    android:id="@+id/btn1"
                    android:layout_width="100dp"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="5dp"
                    android:padding="3dp"
                    android:text="车间着火"/>

                <EditText
                    android:id="@+id/ed1"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:inputType="number"/>


            </LinearLayout>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/img2"
                android:layout_width="200dp"
                android:layout_height="100dp"
                android:layout_marginTop="1dp"
                android:scaleType="fitXY"
                android:src="@color/black"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center"
                android:orientation="vertical">

                <Button
                    android:id="@+id/btn2"
                    android:layout_width="100dp"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="5dp"
                    android:padding="3dp"
                    android:text="仓库着火"/>

                <EditText
                    android:id="@+id/ed2"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:inputType="number"/>


            </LinearLayout>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/img3"
                android:layout_width="200dp"
                android:layout_height="100dp"
                android:layout_marginTop="1dp"
                android:scaleType="fitXY"
                android:src="@color/black"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center"
                android:orientation="vertical">

                <Button
                    android:id="@+id/btn3"
                    android:layout_width="100dp"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="5dp"
                    android:padding="3dp"
                    android:text="楼道着火"/>

                <EditText
                    android:id="@+id/ed3"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:inputType="number"/>


            </LinearLayout>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/img4"
                android:layout_width="200dp"
                android:layout_height="100dp"
                android:layout_marginTop="1dp"
                android:scaleType="fitXY"
                android:src="@color/black"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center"
                android:orientation="vertical">

                <Button
                    android:id="@+id/btn4"
                    android:layout_width="100dp"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="5dp"
                    android:padding="3dp"
                    android:text="食堂着火"/>

                <EditText
                    android:id="@+id/ed4"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:inputType="number"/>


            </LinearLayout>

        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/img5"
                android:layout_width="200dp"
                android:layout_height="100dp"
                android:layout_marginTop="1dp"
                android:scaleType="fitXY"
                android:src="@color/black"/>

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:gravity="center"
                android:orientation="vertical">

                <Button
                    android:id="@+id/btn5"
                    android:layout_width="100dp"
                    android:layout_height="wrap_content"
                    android:layout_marginLeft="5dp"
                    android:padding="3dp"
                    android:text="厨房着火"/>

                <EditText
                    android:id="@+id/ed5"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:inputType="number"/>


            </LinearLayout>

        </LinearLayout>

        <TextView
            android:id="@+id/tv"
            android:layout_width="fill_parent"
            android:layout_height="wrap_content"
            android:layout_gravity="center"
            android:textSize="12sp"
            android:text=""/>

    </LinearLayout>


</RelativeLayout>
```

---

```cpp
package com.zzy.firstapp202_20;

import android.content.Intent;
import android.content.IntentFilter;
import android.os.Bundle;
import android.os.Handler;
import android.text.Editable;
import android.text.TextWatcher;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;
import androidx.localbroadcastmanager.content.LocalBroadcastManager;

public class MainActivity extends AppCompatActivity {

    static final String ReceiverAction = "zzy";
    private LocalBroadcastManager localBroadcastManager;
    MyBroadcastReceiver myBroadcastReceiver;
    private IntentFilter intentFilter;
    private Button btn1, btn2, btn3, btn4, btn5;

    private EditText ed1, ed2, ed3, ed4, ed5;
    private TextView tv;

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
        intentFilter = new IntentFilter();
        intentFilter.addAction(ReceiverAction);
        /*myBroadcastReceiver = new MyBroadcastReceiver();*/
        myBroadcastReceiver = new MyBroadcastReceiver(new MyBroadcastReceiver.BroadcastReceiverCallback() {
            @Override
            public void onMessageReceived(String message) {
                updateTextView(message);
            }
        });
        localBroadcastManager.registerReceiver(myBroadcastReceiver, intentFilter);

        btn1 = findViewById(R.id.btn1);
        btn2 = findViewById(R.id.btn2);
        btn3 = findViewById(R.id.btn3);
        btn4 = findViewById(R.id.btn4);
        btn5 = findViewById(R.id.btn5);

        tv = findViewById(R.id.tv);

        ed1 = findViewById(R.id.ed1);
        ed2 = findViewById(R.id.ed2);
        ed3 = findViewById(R.id.ed3);
        ed4 = findViewById(R.id.ed4);
        ed5 = findViewById(R.id.ed5);

        setupButtonListeners();
        setupEditTextListeners(ed1, "车间");
        setupEditTextListeners(ed2, "仓库");
        setupEditTextListeners(ed3, "楼道");
        setupEditTextListeners(ed4, "食堂");
        setupEditTextListeners(ed5, "厨房");

    }

    private void setupButtonListeners() {
        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                sendBroadcastMessage("车间着火");
            }
        });

        btn2.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                sendBroadcastMessage("仓库着火");
            }
        });

        btn3.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                sendBroadcastMessage("楼道着火");
            }
        });

        btn4.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                sendBroadcastMessage("食堂着火");
            }
        });

        btn5.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                sendBroadcastMessage("厨房着火");
            }
        });
    }

    private void sendBroadcastMessage(String message) {
        Intent intent = new Intent(ReceiverAction);
        intent.putExtra("msg", message);
        localBroadcastManager.sendBroadcast(intent);
    }


    private void setupEditTextListeners(final EditText editText, final String id) {
        TextWatcher textWatcher = new TextWatcher() {
            @Override
            public void beforeTextChanged(CharSequence s, int start, int count, int after) {}

            @Override
            public void onTextChanged(CharSequence s, int start, int before, int count) {}

            @Override
            public void afterTextChanged(Editable s) {
                float value = Float.parseFloat(s.toString());
                if (value > 20) {
                    sendBroadcastMessage(id + ": 温度超过20-- " + "当前温度:" + value);
                }
            }
        };

        editText.addTextChangedListener(textWatcher);
    }

    private void updateTextView(String message) {
        tv.setText(message);
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        localBroadcastManager.unregisterReceiver(myBroadcastReceiver);
    }
}
```

---

```cpp
package com.zzy.firstapp202_20;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.widget.TextView;
import android.widget.Toast;

public class MyBroadcastReceiver extends BroadcastReceiver {


/*    @Override
    public void onReceive(Context context, Intent intent) {

        String msg = intent.getStringExtra("msg");
        Toast.makeText(context, msg, Toast.LENGTH_SHORT).show();
    }*/

    private BroadcastReceiverCallback callback;

    public MyBroadcastReceiver(BroadcastReceiverCallback callback) {
        this.callback = callback;
    }

    @Override
    public void onReceive(Context context, Intent intent) {
        String msg = intent.getStringExtra("msg");
        if (callback != null) {
            callback.onMessageReceived(msg);
        }
    }

    public interface BroadcastReceiverCallback {
        void onMessageReceived(String message);
    }


}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.FirstApp202_20"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <receiver android:name=".MyBroadcastReceiver"
            android:exported="true">
            <intent-filter>
                <action android:name="zzy" />
            </intent-filter>
        </receiver>
    </application>

</manifest>
```

---

![Uploading image.png…]()
