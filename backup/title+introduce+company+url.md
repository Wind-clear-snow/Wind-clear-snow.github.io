```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary" />

    <LinearLayout
        android:id="@+id/mylayout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical">

        <TextView
            android:id="@+id/title"
            android:text="@string/title"
            android:padding="@dimen/titlePadding"
            android:textSize="10sp"
            android:textColor="@color/title"
            android:layout_gravity="center"
            android:gravity="center"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

        <TextView
            android:id="@+id/introduce"
            android:text="@string/introduce"
            android:textSize="@dimen/introduce"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content" />

        <TextView
            android:id="@+id/company"
            android:text="@string/company"
            android:gravity="center"
            android:textColor="@color/company"
            android:padding="@dimen/padding"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

        <TextView
            android:id="@+id/url"
            android:text="@string/url"
            android:gravity="center"
            android:textColor="@color/url"
            android:padding="@dimen/padding"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"/>

    </LinearLayout>

</LinearLayout>
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="title">#FF888888</color>
    <color name="introduce">#7e8</color>
    <color name="company">#f70</color>
    <color name="url">#9f60</color>
    <color name="colorPrimary">#3F51B5</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
</resources>
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
<resources>
    <string name="app_name">FirstApp202_18</string>
    <string name="title">ikun</string>
    <string name="introduce">蔡徐坤（KUN），1998年8月2日出生于浙江省温州市，户籍湖南省吉首市， [114]中国内地男歌手、演员、原创音乐制作人、 [1]MV导演。</string>
    <string name="company">cai xu kun</string>
    <string name="url">www.ikun.com</string>
</resources>
```

---

```cpp
package com.zzy.firstapp202_18;

import android.annotation.SuppressLint;
import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.LinearLayout;
import android.widget.TextView;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private LinearLayout mylayout;
    private TextView title, introduce, company, url;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);

        // 找到Toolbar视图
        Toolbar toolbar = findViewById(R.id.toolbar);
        // 设置为活动的操作栏
        setSupportActionBar(toolbar);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        mylayout = findViewById(R.id.mylayout);
        title = findViewById(R.id.title);
        introduce = findViewById(R.id.introduce);
        company = findViewById(R.id.company);
        url = findViewById(R.id.url);
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

                title.setTextSize(30);
                title.setTextColor(Color.BLACK);


                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.red:
                mylayout.setBackgroundColor(Color.RED);

                introduce.setTextSize(20);
                introduce.setTextColor(getResources().getColor(R.color.introduce));

                Toast.makeText(this, "你选中了"+item.getItemId(), Toast.LENGTH_SHORT).show();
                break;
            case R.id.item3:
                mylayout.setBackgroundColor(Color.WHITE);

                title.setTextColor(getResources().getColor(R.color.title));
                title.setTextSize(getResources().getDimension(R.dimen.title));

                introduce.setTextSize(getResources().getDimension(R.dimen.introduce));
                introduce.setTextColor(Color.BLACK);

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

![QQ20241118-170122](https://github.com/user-attachments/assets/1e03abfe-ecbb-4baf-ae69-9649c89cd637)
