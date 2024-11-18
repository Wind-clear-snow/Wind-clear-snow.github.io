```cpp
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item android:id="@+id/red" android:title="红色"></item>
    <item android:id="@+id/blue" android:title="蓝色"></item>
    <item android:id="@+id/green" android:title="绿色"></item>
    <item android:id="@+id/yellow" android:title="黄色"></item>
    <item android:id="@+id/gray" android:title="灰色"></item>
    <item android:id="@+id/white" android:title="白色"></item>
    <item android:id="@+id/def" android:title="恢复默认"></item>
</menu>
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:padding="5px"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/show"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:textSize="28px"
        android:text="打开菜单~~~~" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_17;

import android.graphics.Color;
import android.os.Bundle;
import android.view.ContextMenu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private TextView show;

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

        show = findViewById(R.id.show);
        registerForContextMenu(show);
    }

    @Override
    public void onCreateContextMenu(ContextMenu menu, View v, ContextMenu.ContextMenuInfo menuInfo) {
        super.onCreateContextMenu(menu, v, menuInfo);
        MenuInflater inflater = new MenuInflater(this);
        inflater.inflate(R.menu.contextmenu, menu);
        menu.setHeaderIcon(R.drawable.ic_launcher_background);
        menu.setHeaderTitle("选择文字颜色");
    }

    @Override
    public boolean onContextItemSelected(@NonNull MenuItem item) {

        switch (item.getItemId()) {
            case R.id.red:
                show.setTextColor(Color.RED);
                break;
            case R.id.blue:
                show.setTextColor(Color.BLUE);
                break;
            case R.id.green:
                show.setTextColor(Color.GREEN);
                break;
            case R.id.yellow:
                show.setTextColor(Color.YELLOW);
                break;
            case R.id.gray:
                show.setTextColor(Color.GRAY);
                break;
            case R.id.white:
                show.setTextColor(Color.WHITE);
                break;
            default:
                show.setTextColor(Color.BLACK);
        }

        return true;
    }
}
```

---

![Uploading 图片1.png…]()


