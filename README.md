# Ex.No:6 Implement an application that uses Explicit Intent using Android


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “contentprovider″ and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: KISHORE M
Registeration Number : 212222040079
*/
```



### Main activity.java:
```
package com.example.ex6;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

import android.content.Intent;

import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    EditText e1;
    Button res;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        e1=findViewById(R.id.editTextPersonName);
        res=findViewById(R.id.button);
        res.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view)
            {
                int n1=Integer.parseInt(e1.getText().toString());
                int sum =1;
                while(n1!=0)
                {
                    sum = sum * n1;
                    n1--;
                }
                Intent intent=new Intent(getApplicationContext(),SecondActivity.class);
                intent.putExtra("key",sum);
                startActivity(intent);
            }
        });
    }
}
```
### second activity.java:
```
package com.example.ex6;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.content.Intent;
import android.widget.TextView;



public class SecondActivity extends AppCompatActivity {
    TextView t1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
        t1=findViewById(R.id.textView);
        Intent intent=getIntent();
        int result=intent.getIntExtra("key",0);
        t1.setText(Integer.toString(result));
    }
}
```
### activity main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/relativeLayout"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:visibility="visible"
    tools:context=".MainActivity"
    tools:visibility="visible">


    <TextView
        android:id="@+id/textview"
        android:layout_width="248dp"
        android:layout_height="55dp"
        android:fontFamily="sans-serif-black"
        android:lineSpacingExtra="12sp"
        android:text="ENTER THE NUMBER"
        android:textAppearance="@style/TextAppearance.AppCompat.Large"
        android:textColor="#E91E63"
        android:textSize="20sp"
        android:textStyle="bold"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.671"
        tools:layout_editor_absoluteX="97dp"
        tools:layout_editor_absoluteY="175dp" />

    <EditText
        android:id="@+id/editTextPersonName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="textPersonName"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.671" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.622" />

</android.support.constraint.ConstraintLayout>
```
### activity second.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/relativeLayout2"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="147dp"
        android:layout_height="23dp"
        android:fontFamily="sans-serif-black"
        android:text="TextView"
        android:textColor="#E91E63"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.856"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.447" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-black"
        android:text="Factorial is  : "
        android:textAlignment="textEnd"
        android:textAllCaps="true"
        android:textSize="20sp"
        android:textStyle="italic"
        android:typeface="normal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.171"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.45" />
</android.support.constraint.ConstraintLayout>
```
### Android  manifest:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.ex6">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Ex6"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
            <activity android:name=".SecondActivity" />
    </application>

</manifest>
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/8ee84c91-2776-4df4-9c86-e20fbc1a7fca)
![image](https://github.com/user-attachments/assets/9dd886bf-9db6-4580-8e23-f5ae361b3bda)
![image](https://github.com/user-attachments/assets/93532a94-b734-4848-8e05-cb4902f371c0)


## RESULT:
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
