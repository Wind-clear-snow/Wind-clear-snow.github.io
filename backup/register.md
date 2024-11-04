```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="用户名:" />

    <EditText
        android:id="@+id/user"
        android:minWidth="200px"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:inputType="text"/>

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="密码:" />

    <EditText
        android:id="@+id/pwd"
        android:minWidth="200px"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:inputType="textPassword"/>

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="密码:" />

    <EditText
        android:id="@+id/repwd"
        android:minWidth="200px"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:inputType="textPassword"/>

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="电话号码"/>

    <EditText
        android:id="@+id/phone"
        android:minWidth="200px"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:inputType="text"/>

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="邮箱:" />

    <EditText
        android:id="@+id/email"
        android:minWidth="200px"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:inputType="textEmailAddress"/>

    <Button
        android:id="@+id/btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="注册" />


</LinearLayout>
```

---

```cpp
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".RegisterActivity">

    <TextView
        android:id="@+id/user"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="10px"
        android:text="用户名" />

    <TextView
        android:id="@+id/pwd"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="10px"
        android:text="密码" />

    <TextView
        android:id="@+id/phone"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="10px"
        android:text="手机号" />

    <TextView
        android:id="@+id/email"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="10px"
        android:text="邮箱" />

    <Button
        android:id="@+id/back"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:padding="10px"
        android:text="返回" />

</LinearLayout>
```

---

```cpp
package com.zzy.firstapp202_14;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class MainActivity extends AppCompatActivity {

    final public int CODE = 0x001;
    private EditText eduser, edpwd, edrepwd, edphone, edemail;

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

        Button register = findViewById(R.id.btn);
        register.setOnClickListener(new View.OnClickListener() {

            @Override
            public void onClick(View view) {

                eduser = findViewById(R.id.user);
                String user = eduser.getText().toString();

                edpwd = findViewById(R.id.pwd);
                String pwd = edpwd.getText().toString();

                edrepwd = findViewById(R.id.repwd);
                String repwd = edrepwd.getText().toString();

                edphone = findViewById(R.id.phone);
                String phone = edphone.getText().toString();

                edemail = findViewById(R.id.email);
                String email = edemail.getText().toString();


                if (user.equals("") || pwd.equals("") || repwd.equals("") || phone.equals("") || email.equals("")) {
                    Toast.makeText(MainActivity.this, "请输入完整信息", Toast.LENGTH_SHORT).show();
                    return;
                }

                if (!pwd.equals(repwd)) {
                    Toast.makeText(MainActivity.this, "两次密码不一致", Toast.LENGTH_SHORT).show();
                    edpwd.setText("");
                    edrepwd.setText("");
                    edpwd.requestFocus();
                    return;
                }

                if (!isValidPhone(phone)) {
                    Toast.makeText(MainActivity.this, "请输入正确的电话号码格式", Toast.LENGTH_SHORT).show();
                    edphone.setText("");
                    edphone.requestFocus();
                    return;
                }

                if (!isValidEmail(email)) {
                    Toast.makeText(MainActivity.this, "请输入正确的邮箱格式", Toast.LENGTH_SHORT).show();
                    edemail.setText("");
                    edemail.requestFocus();
                    return;
                }

                int passwordStrength = checkPasswordStrength(pwd);
                if (passwordStrength == 0) {
                    Toast.makeText(MainActivity.this, "密码过于简单，请重新输入", Toast.LENGTH_SHORT).show();
                    edpwd.setText("");
                    edrepwd.setText("");
                    edpwd.requestFocus();
                    return;
                }else if (passwordStrength == 1) {
                    Toast.makeText(MainActivity.this, "密码强度较弱", Toast.LENGTH_SHORT).show();
                }else if (passwordStrength == 2) {
                    Toast.makeText(MainActivity.this, "密码强度适中", Toast.LENGTH_SHORT).show();
                }

                Intent intent = new Intent(MainActivity.this, RegisterActivity.class);
                Bundle bundle = new Bundle();
                bundle.putString("user", user);
                bundle.putString("pwd", pwd);
                bundle.putString("phone", phone);
                bundle.putString("email", email);
                intent.putExtras(bundle);
                startActivityForResult(intent, CODE);

            }
        });
    }

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == CODE && resultCode == RESULT_OK) {
            edpwd.setText("");
            edrepwd.setText("");
            Toast.makeText(MainActivity.this, "注册成功", Toast.LENGTH_SHORT).show();
        }
    }


    private boolean isValidPhone(String phone) {
        String phoneRegex = "^1[3-9]\\d{9}$";
        Pattern pattern = Pattern.compile(phoneRegex);
        Matcher matcher = pattern.matcher(phone);
        return matcher.matches();
    }


    private boolean isValidEmail(String email) {
        String emailRegex = "^[a-zA-Z0-9_.-]+@[a-zA-Z0-9-]+(\\.[a-zA-Z0-9-]+)*\\.[a-zA-Z0-9]{2,6}$";
        Pattern pattern = Pattern.compile(emailRegex);
        Matcher matcher = pattern.matcher(email);
        return matcher.matches();
    }


    private int checkPasswordStrength(String password) {
        if (password.length() < 8) {
            return 0;
        } else if (password.matches(".*[A-Z].*") && password.matches(".*[a-z].*") && password.matches(".*\\d.*")) {
            return 2;
        } else if (password.matches(".*[A-Z].*") || password.matches(".*[a-z].*") || password.matches(".*\\d.*")) {
            return 1;
        } else {
            return 0;
        }
    }
}
```

---

```cpp
package com.zzy.firstapp202_14;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class RegisterActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_register);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });

        final Intent intent = getIntent();
        Bundle bundle = intent.getExtras();
        TextView user = findViewById(R.id.user);
        user.setText("用户名：" + bundle.getString("user"));
        TextView pwd = findViewById(R.id.pwd);
        pwd.setText("密码:" + bundle.getString("pwd"));
        TextView phone = findViewById(R.id.phone);
        phone.setText("电话:" + bundle.getString("phone"));
        TextView email = findViewById(R.id.email);
        email.setText("邮箱:" + bundle.getString("email"));

        Button button = findViewById(R.id.back);
        button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                setResult(RESULT_OK,intent);
                finish();
            }
        });
    }
}
```

---

![image](https://github.com/user-attachments/assets/b7f965e6-e159-45f4-8681-8b5e9bcfe160)

