···cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity">

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="显示投票对话框" />

        <TextView
            android:id="@+id/Details"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="反对：0--赞成：0--弃权：0 " />


    </LinearLayout>

    <Button
        android:id="@+id/btn2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示带列表的对话框" />

    <Button
        android:id="@+id/btn3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示带单选列表的对话框" />

    <Button
        android:id="@+id/btn4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="显示带多选列表的对话框" />


</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_15;

import android.content.DialogInterface;
import android.os.Bundle;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;
import android.app.AlertDialog;
import android.app.AlertDialog.Builder;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {

    private boolean[] checkedItems;
    private int check = -1;
    private String[] items;
    private Button btn1, btn2, btn3, btn4;
    private TextView tv;
    private int x=0,y=0,z=0;

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

        tv = findViewById(R.id.Details);

        btn1 = findViewById(R.id.btn1);

        btn1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                AlertDialog alert = new AlertDialog.Builder(MainActivity.this).create();
                alert.setIcon(R.drawable.ic_launcher_foreground);
                alert.setTitle("投票提示:");
                alert.setMessage("你确定要投票吗？");

                alert.setButton(DialogInterface.BUTTON_NEGATIVE, "反对", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        y++;
                        tv.setText("反对：" + y + "--"+ " 赞成：" + x + "--" + "弃权：" + z);
                        Toast.makeText(MainActivity.this, "反对投票", Toast.LENGTH_SHORT).show();
                    }
                });

                alert.setButton(DialogInterface.BUTTON_POSITIVE, "赞成", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        x++;
                        tv.setText("反对：" + y + "--"+ " 赞成：" + x + "--" + "弃权：" + z);
                        Toast.makeText(MainActivity.this, "投票成功", Toast.LENGTH_SHORT).show();
                    }
                });


                alert.setButton(DialogInterface.BUTTON_NEUTRAL, "弃权", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        z++;
                        tv.setText("反对：" + y + "--"+ " 赞成：" + x + "--" + "弃权：" + z);
                        Toast.makeText(MainActivity.this, "弃权成功", Toast.LENGTH_SHORT).show();
                    }
                });

                alert.show();
            }
        });

        btn2 = findViewById(R.id.btn2);
        btn2.setOnClickListener(new OnClickListener() {

            @Override
            public void onClick(View view) {
                final String[] items = {"跑步", "羽毛球", "乒乓球", "网球", "体操", "篮球", "足球"};
                Builder builder = new Builder(MainActivity.this);
                builder.setIcon(R.drawable.ic_launcher_background);
                builder.setTitle("请选择你的爱好");
                builder.setItems(items, new DialogInterface.OnClickListener() {

                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        Toast.makeText(MainActivity.this, "选择了"+items[i], Toast.LENGTH_SHORT).show();
                        btn2.setText(items[i]);
                    }
                });
                builder.create().show();
            }
        });


        btn3 = findViewById(R.id.btn3);
        btn3.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View view) {
                final String[] items = new String[] {"标准","无声","会议","户外","离线"};
                Builder builder = new Builder(MainActivity.this);
                builder.setIcon(R.drawable.ic_launcher_background);
                builder.setTitle("请选择要使用发情景模式:");
                builder.setSingleChoiceItems(items,check, new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        check = i;
                        Toast.makeText(MainActivity.this, items[i], Toast.LENGTH_SHORT).show();
                        btn3.setText(items[i] + "模式");
                    }

                });
                builder.create().show();
            }
        });

        btn4 = findViewById(R.id.btn4);
        checkedItems = new boolean[] {false, false, false, false, false};
        btn4.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View view) {
                final String[] items = new String[]{"植物大战僵尸", "泡泡龙", "开心农场", "超级玛丽", "愤怒的小鸟"};

                Builder builder = new Builder(MainActivity.this);
                builder.setIcon(R.drawable.ic_launcher_background);
                builder.setTitle("请选择要游玩的游戏:");
                builder.setMultiChoiceItems(items, checkedItems, new DialogInterface.OnMultiChoiceClickListener() {

                    @Override
                    public void onClick(DialogInterface dialogInterface, int i, boolean b) {
                        checkedItems[i] = b;
                    }
                });

                builder.setPositiveButton("确定", new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialogInterface, int i) {
                        String result = "";
                        for (int j = 0; j < items.length; j++) {
                            if (checkedItems[j]) {
                                result += items[j] + ",";

                            }
                        }

                        if (!"".equals(result)){
                            result = result.substring(0, result.length() - 1);
                            Toast.makeText(MainActivity.this, "你选择了：" + result, Toast.LENGTH_SHORT).show();
                        }
                    }
                });
                builder.create().show();
            }
        });

    }
}
```

---

![image](https://github.com/user-attachments/assets/36dabb1f-61ef-4358-9ff7-39af5b0494b6)
