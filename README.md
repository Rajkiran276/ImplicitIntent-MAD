# Ex.No:3a Develop program to create a text field and a button “Navigate”. When you enter “www.gmail.com” and press navigate button it should open google page using Implicit Intents.

## AIM:

To create a navigate button using Implicit Intent to display the gmail page using Android Studio.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Here’s the algorithm in single-line points:

1. Create a new Android project with an Empty Activity.
2. Add an `EditText` for URL input in `activity_main.xml`.
3. Add a `Button` labeled “Navigate” in the layout.
4. Link `EditText` and `Button` in `MainActivity` using `findViewById()`.
5. Set an `OnClickListener` on the “Navigate” button.
6. On click, read text from `EditText` and validate it.
7. Prepend “https://” if the URL doesn’t start with it.
8. Create an implicit intent with `Intent.ACTION_VIEW` and the URL as `Uri`.
9. Call `startActivity(intent)` to open the browser.


## PROGRAM:
```
/*
Program to print the text “Implicitintent”.
Developed by: THARSHAN R
Registeration Number : 212223223004
*/
```


Main activity.java

```

package com.example.exp_02;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText editTextURL;
    Button btnOpen;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextURL = findViewById(R.id.editTextURL);
        btnOpen = findViewById(R.id.btnOpen);

        btnOpen.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String url = editTextURL.getText().toString().trim();

                // If URL doesn’t start with http/https, add it
                if (!url.startsWith("http://") && !url.startsWith("https://")) {
                    url = "http://" + url;
                }

                // Implicit Intent to open URL
                Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse(url));
                startActivity(intent);
            }
        });
    }
}


```
Android manifest.xml
```

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
        android:theme="@style/Theme.EXP02">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```


## OUTPUT
<img width="1920" height="1200" alt="Screenshot (69)" src="https://github.com/user-attachments/assets/3f964b2a-cb3a-4913-93b4-7d1f1aabec28" />





## RESULT
Thus a Simple Android Application create a navigate button using Implicit Intent to display the gmail page using Android Studio is developed and executed successfully.


