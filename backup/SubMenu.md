```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20dp"
        android:text="长按该文本弹出一级菜单" />

    <ImageView
        android:id="@+id/img"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

</LinearLayout>
```

---

```cpppackage com.zzy.firstapp202_19;

import android.os.Bundle;
import android.view.ContextMenu;
import android.view.MenuItem;
import android.view.SubMenu;
import android.view.View;
import android.widget.ImageView;
import android.widget.TextView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private ImageView img;

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

        TextView tv = findViewById(R.id.tv);
        img = findViewById(R.id.img);
        registerForContextMenu(tv);
    }

    @Override
    public void onCreateContextMenu(ContextMenu menu, View v, ContextMenu.ContextMenuInfo menuInfo) {
        super.onCreateContextMenu(menu, v, menuInfo);
        menu.setHeaderTitle("一级菜单");
        SubMenu sub1 = menu.addSubMenu("游戏角色选择");
        sub1.add(0, sub1.FIRST+1, 1, "刘备");
        sub1.add(0, sub1.FIRST+2, 2, "关羽");
        sub1.add(0, sub1.FIRST+3, 3, "张飞");
        SubMenu sub2 = menu.addSubMenu("游戏道具选择");
        sub2.add(0, sub2.FIRST+4, 1, "桃");
        sub2.add(0, sub2.FIRST+5, 2, "酒");
        sub2.add(0, sub2.FIRST+6, 3, "杀");
        SubMenu sub3 = menu.addSubMenu("进攻疆土");
        sub3.add(0, sub3.FIRST+7, 1, "魏");
        sub3.add(0, sub3.FIRST+8, 2, "蜀");
        sub3.add(0, sub3.FIRST+9, 3, "吴");

    }

    @Override
    public boolean onContextItemSelected(@NonNull MenuItem item) {

        switch (item.getItemId()) {
            case SubMenu.FIRST+1:
                img.setImageResource(R.drawable.liubei);
                break;
            case SubMenu.FIRST+2:
                img.setImageResource(R.drawable.guanyu);
                break;
            case SubMenu.FIRST+3:
                img.setImageResource(R.drawable.zhangfei);
                break;
            case SubMenu.FIRST+4:
                img.setImageResource(R.drawable.tao);
                break;
            case SubMenu.FIRST+5:
                img.setImageResource(R.drawable.jiu);
                break;
            case SubMenu.FIRST+6:
                img.setImageResource(R.drawable.sha);
                break;
            case SubMenu.FIRST+7:
                img.setImageResource(R.drawable.wushuang);
                Toast.makeText(MainActivity.this, "睡觉", Toast.LENGTH_SHORT).show();
                break;
            case SubMenu.FIRST+8:
                img.setImageResource(R.drawable.jgtao);
                Toast.makeText(MainActivity.this, "睡觉", Toast.LENGTH_SHORT).show();
                break;
            case SubMenu.FIRST+9:
                img.setImageResource(R.drawable.sunboy);
                Toast.makeText(MainActivity.this, "睡觉", Toast.LENGTH_SHORT).show();
                break;

        }

        return true;
    }
}
```

---

![123456](https://github.com/user-attachments/assets/8841cecc-8ad7-417f-ac46-158b0007199e)
