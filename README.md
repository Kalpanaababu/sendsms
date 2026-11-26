
# Ex.No:6 Design an android application Send SMS using Intent.


## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
Program to create and design an android application Send SMS using Intent.
Developed by: KALPANAA BABU TM
Registeration Number : 212224230112
```
## MAINACTIVITY.JAVA:
```
package com.example.mysms;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText phone, message;
    Button send;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        phone = findViewById(R.id.phone);
        message = findViewById(R.id.message);
        send = findViewById(R.id.send);

        send.setOnClickListener(v -> {
            String number = phone.getText().toString().trim();
            String msg = message.getText().toString().trim();

            if (number.isEmpty() || msg.isEmpty()) {
                Toast.makeText(this,
                        "Enter phone number and message",
                        Toast.LENGTH_SHORT).show();
                return;
            }

            Intent intent = new Intent(
                    Intent.ACTION_SENDTO,
                    Uri.parse("smsto:" + Uri.encode(number))
            );

            intent.putExtra("sms_body", msg);

            try {
                startActivity(intent);
            } catch (android.content.ActivityNotFoundException e) {
                Toast.makeText(this,
                        "No SMS application found",
                        Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```
## ACTIVITY_MAIN.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp"
    android:background="#F3E5F5">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="28sp"
        android:textStyle="bold"
        android:textColor="#212121"
        android:layout_marginBottom="24dp"
        tools:ignore="HardcodedText" />

    <com.google.android.material.card.MaterialCardView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:cardCornerRadius="16dp"
        app:cardElevation="6dp"
        app:cardBackgroundColor="#FFFFFF"
        app:strokeWidth="0dp">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            android:padding="20dp">

            <com.google.android.material.textfield.TextInputLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter Mobile Number"
                style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"
                android:layout_marginBottom="16dp">

                <com.google.android.material.textfield.TextInputEditText
                    android:id="@+id/phone"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:inputType="phone"
                    android:textColor="#000000"
                    android:textColorHint="#757575" />

            </com.google.android.material.textfield.TextInputLayout>

            <com.google.android.material.textfield.TextInputLayout
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:hint="Enter the Message"
                style="@style/Widget.MaterialComponents.TextInputLayout.OutlinedBox"
                android:layout_marginBottom="20dp">

                <com.google.android.material.textfield.TextInputEditText
                    android:id="@+id/message"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:inputType="textMultiLine"
                    android:minLines="3"
                    android:gravity="top"
                    android:textColor="#000000"
                    android:textColorHint="#757575" />

            </com.google.android.material.textfield.TextInputLayout>

            <com.google.android.material.button.MaterialButton
                android:id="@+id/send"
                android:layout_width="match_parent"
                android:layout_height="56dp"
                android:text="Send SMS"
                android:textSize="16sp"
                android:textStyle="bold"
                app:cornerRadius="12dp"
                android:backgroundTint="#7B1FA1"
                android:textColor="#FFFFFF" />

        </LinearLayout>

    </com.google.android.material.card.MaterialCardView>

</LinearLayout>
```
## ANDROIDMANIFEST.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <queries>
        <intent>
            <action android:name="android.intent.action.SENDTO" />
            <data android:scheme="smsto" />
        </intent>
    </queries>

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MySms">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>

```


## OUTPUT

<img width="1917" height="1140" alt="image" src="https://github.com/user-attachments/assets/99c46675-f769-41d8-9d08-9bca9a5e93b4" />

<img width="1917" height="1140" alt="image" src="https://github.com/user-attachments/assets/66824291-ad9b-4f30-a75c-37e84e1c4488" />

<img width="1917" height="1140" alt="image" src="https://github.com/user-attachments/assets/b05d076d-0790-4abc-b3d2-742d8b210552" />




## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
