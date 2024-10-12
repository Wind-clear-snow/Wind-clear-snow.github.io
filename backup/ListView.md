```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/listView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:entries="@array/cTypes" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content" />

</LinearLayout>
```

---

```cpp
<resources>
    <string name="app_name">FirstApp202_10</string>
    <string-array name="cTypes">
        <item>Food</item>
        <item>Entertainment</item>
        <item>Transportation</item>
    </string-array>
</resources>
```

---

```cpp
package com.zzy.firstapp202_10;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
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

        ListView listView = findViewById(R.id.listView);
        TextView textView = findViewById(R.id.textView);
        String[] cType = {"唱", "跳", "Rap", "篮球", "kunkun"};
        ArrayAdapter<String> adapter = new ArrayAdapter<>(this, android.R.layout.simple_list_item_1, cType);
        listView.setAdapter(adapter);

        listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View arg1, int position, long id) {
                textView.setText("");
                Toast.makeText(MainActivity.this, "你点击了第" + (position + 1) + "项", Toast.LENGTH_SHORT).show();
                String result = parent.getItemAtPosition(position).toString();
                Toast.makeText(MainActivity.this, "你点击了" + result, Toast.LENGTH_SHORT).show();
                textView.setText("选中的是" + result);
            }
        });
    }

}
```

---

![image](https://github.com/user-attachments/assets/a2874488-f0dc-41d8-8996-8a33ce8d1b51)

