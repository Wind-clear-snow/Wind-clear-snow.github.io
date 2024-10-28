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
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="首发页面" />

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="启动一个Activity" />

        <Button
            android:id="@+id/btn2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="启动多个Activity" />
    </LinearLayout>

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_12;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;

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

        Button btn1 = findViewById(R.id.btn1);
        btn1.setOnClickListener(Listener1);

        Button btn2 = findViewById(R.id.btn2);
        btn2.setOnClickListener(Listener2);

    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.i("MainActivity", "MainActivity ==> onResume: ");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.i("MainActivity","MainActivity ==> onPause");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.i("MainActivity","MainActivity ==> onDestroy");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.i("MainActivity","MainActivity ==> onStop");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.i("MainActivity","MainActivity ==> onRestart");
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.i("MainActivity","MainActivity ==> onStart");
    }

    private View.OnClickListener Listener1 = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent intent = new Intent();
            intent.setClass(MainActivity.this, FirstActivity.class);
            startActivity(intent);
        }
    };

    private View.OnClickListener Listener2 = new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            Intent intent1 = new Intent();
            intent1.setClass(MainActivity.this, FirstActivity.class);
            Intent intent2 = new Intent();
            intent2.setClass(MainActivity.this, SecondActivity.class);
            Intent[] intents = {intent1,intent2};
            startActivities(intents);

        }
    };
}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    tools:context=".FirstActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="FirstActivity" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_12;

import android.os.Bundle;
import android.util.Log;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class FirstActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_first);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });


    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.i("FirstActivity","FirstActivity ==> onStart");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.i("FirstActivity","FirstActivity ==> onStop");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.i("FirstActivity","FirstActivity ==> onDestroy");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.i("FirstActivity","FirstActivity ==> onPause");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.i("FirstActivity","FirstActivity ==> onResume");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.i("FirstActivity","FirstActivity ==> onRestart");
    }
}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    tools:context=".SecondActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SecondActivity" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_12;

import android.os.Bundle;
import android.util.Log;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_second);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.i("SecondActivity","SecondActivity ==> onStart");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.i("SecondActivity","SecondActivity ==> onStop");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.i("SecondActivity","SecondActivity ==> onPause");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.i("SecondActivity","SecondActivity ==> onResume");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.i("SecondActivity","SecondActivity ==> onDestroy");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.i("SecondActivity","SecondActivity ==> onRestart");
    }
}
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools" >

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.FirstApp202_12"
        tools:targetApi="31" >
        <activity
            android:name=".FirstActivity"
            android:label="第一个活动"
            android:exported="false" />
        <activity
            android:name=".SecondActivity"
            android:exported="false"
            android:label="第二个活动" />
        <activity
            android:name=".MainActivity"
            android:exported="true" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

---

![image](https://github.com/user-attachments/assets/0e9f2ef1-2b01-4cfd-88eb-9442da927eb0)
