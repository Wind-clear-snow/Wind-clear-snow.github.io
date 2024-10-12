```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <GridView
        android:scrollbars="vertical"
        android:id="@+id/gridview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:stretchMode="columnWidth"
        android:numColumns="1"/>

</LinearLayout>
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal">

    <LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:orientation="vertical">
        <ImageView
            android:id="@+id/image"
            android:layout_width="75px"
            android:layout_height="75px"
            android:scaleType="fitCenter"
            android:padding="10px"/>

        <TextView
            android:id="@+id/title"
            android:layout_width="75px"
            android:layout_height="75px"
            android:layout_gravity="center"
            android:textSize="10dp"
            android:padding="5px"/>
    </LinearLayout>

    <TextView
        android:id="@+id/introduce"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center"
        android:padding="5px"/>

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_11;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.AdapterView;
import android.widget.GridView;
import android.widget.SimpleAdapter;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

public class MainActivity extends AppCompatActivity {

    private int[] imageId = {R.drawable.apple, R.drawable.banana, R.drawable.orange, R.drawable.pear,
                            R.drawable.grape, R.drawable.watermelon, R.drawable.pineapple, R.drawable.mango,
                            R.drawable.strawberry, R.drawable.blueberry, R.drawable.kiwi, R.drawable.peach};

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

        GridView gridView = findViewById(R.id.gridview);
        String[] title = {"apple", "banana", "orange", "pear",
                          "grape", "watermelon", "pineapple", "mango",
                          "strawberry", "blueberry", "kiwi", "peach"};

        String[] introduce = {"产地:中国 价格:5", "产地:中国 价格:3", "产地:中国 价格:4", "产地:中国 价格:6",
                              "产地:中国 价格:7", "产地:中国 价格:8", "产地:中国 价格:9", "产地:中国 价格:10",
                            "产地:中国 价格:11", "产地:中国 价格:12", "产地:中国 价格:13", "产地:中国 价格:14"};

        List<Map<String, Object>> listItems = new ArrayList<Map<String, Object>>();

        for (int i = 0; i < imageId.length; i++) {
            Map<String, Object> listItem = new HashMap<String, Object>();
            listItem.put("image", imageId[i]);
            listItem.put("title", title[i]);
            listItem.put("introduce", "属性:"+introduce[i]);
            listItems.add(listItem);
        }

        SimpleAdapter adapter = new SimpleAdapter(this,
                                                listItems,
                                                R.layout.items,
                                                new String[]{"title", "image", "introduce"},
                                                new int[]{R.id.title, R.id.image, R.id.introduce});

        gridView.setAdapter(adapter);
        gridView.setOnItemClickListener(new AdapterView.OnItemClickListener() {
            @Override
            public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
                String result = parent.getItemAtPosition(position).toString();
                Map<String, Object> map = listItems.get(position);
                Toast.makeText(MainActivity.this,
                        "您选择了第" + String.valueOf(position+1) + map.get("title").toString(),
                             Toast.LENGTH_SHORT).show();
                Log.i("GridView","result" + result);
            }
        });
    }
}
```

---

![image](https://github.com/user-attachments/assets/724e5c8d-ed75-40a2-a326-6accbef4462d)
