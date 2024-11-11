```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <LinearLayout
        android:id="@+id/mylayout"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        android:orientation="vertical">

    </LinearLayout>

</LinearLayout>
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item android:id="@+id/item1" android:title="更换背景" android:alphabeticShortcut="g">
        <menu>
            <group android:id="@+id/back" android:checkableBehavior="all">
                <item android:id="@+id/blue" android:title="蓝色" />
                <item android:id="@+id/red" android:title="红色" />
            </group>
        </menu>
    </item>

    <item android:id="@+id/item2" android:title="参数设置" android:alphabeticShortcut="e">
        <menu>
            <group android:id="@+id/setting" android:checkableBehavior="all">
                <item android:id="@+id/background" android:title="使用背景" />
                <item android:id="@+id/music" android:title="背景音乐" />
            </group>
        </menu>
    </item>
    <item android:id="@+id/item3" android:title="恢复默认" android:alphabeticShortcut="r" />

</menu>
```

---

```cpp
package com.zzy.firstapp202_16;

import android.annotation.SuppressLint;
import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.LinearLayout;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private LinearLayout mylayout;

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

        mylayout = findViewById(R.id.mylayout);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = new MenuInflater(this);
        inflater.inflate(R.menu.optionmenu, menu);
        return true;
    }

    @SuppressLint("NonConstantResourceId")
    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        if (item.getItemId() == R.id.setting) {
            if (item.isChecked()){
                item.setChecked(false);
            }else {
                item.setChecked(true);
            }
        }

        switch (item.getItemId()) {
            case R.id.blue:
                mylayout.setBackgroundColor(Color.BLUE);
                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.red:
                mylayout.setBackgroundColor(Color.RED);
                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.item3:
                mylayout.setBackgroundColor(Color.WHITE);
                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.background:
                mylayout.setBackgroundResource(R.drawable.ic_launcher_background);
                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.music:
                final String[] items = {"唱", "跳", "rap", "篮球", "music", "i", "kun"};
                AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
                builder.setIcon(R.drawable.ic_launcher_background);
                builder.setTitle("请选择音乐");
                builder.setItems(items, new DialogInterface.OnClickListener() {

                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        Toast.makeText(MainActivity.this, "选择了"+items[i], Toast.LENGTH_SHORT).show();
                    }
                });
                builder.create().show();
                break;
        }
                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();

        return super.onOptionsItemSelected(item);
    }
}
```

---
F10
![image](https://github.com/user-attachments/assets/720fcd85-0e48-4b4e-b4d1-6f66a57a978e)
