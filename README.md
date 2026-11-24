# Ex.No: 11 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

1. Create a new Android Studio project.
2. Design the layout with an ImageView and buttons for different animations.
3. Initialize the ImageView and buttons in MainActivity.java.
4. Set click listeners for each button to perform the corresponding animation.
5. Implement blink, rotate, fade, move, slide, and zoom animations using XML files.
6. Use the Stop button to stop the running animation.
7. Run the application and verify all animations.


## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: Junjar U
Registeration Number : 212224230110
*/
```

## activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <LinearLayout
        xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:gravity="center_horizontal"
        tools:context=".MainActivity">

        <ImageView
            android:id="@+id/imageview"
            android:layout_width="200dp"
            android:layout_height="200dp"
            android:layout_marginTop="40dp"
            android:contentDescription="@string/app_name"
            android:src="@drawable/ic_launcher_foreground" />

        <LinearLayout
            android:id="@+id/linear1"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="30dp"
            android:orientation="horizontal"
            android:weightSum="3">

            <!--To start the blink animation of the image-->
            <Button
                android:id="@+id/blink"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/blink"
                android:textColor="@color/white" />

            <!--To start the rotate animation of the image-->
            <Button
                android:id="@+id/rotate"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/clockwise"
                android:textColor="@color/white" />

            <!--To start the fading animation of the image-->
            <Button
                android:id="@+id/fade"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/fade"
                android:textColor="@color/white" />

        </LinearLayout>

        <LinearLayout
            android:id="@+id/linear2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="30dp"
            android:orientation="horizontal"
            android:weightSum="3">

            <!--To start the move animation of the image-->
            <Button
                android:id="@+id/move"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/move"
                android:textColor="@color/white" />

            <!--To start the slide animation of the image-->
            <Button
                android:id="@+id/slide"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/slide"
                android:textColor="@color/white" />

            <!--To start the zoom animation of the image-->
            <Button
                android:id="@+id/zoom"
                style="@style/TextAppearance.MaterialComponents.Button"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:layout_margin="10dp"
                android:layout_weight="1"
                android:padding="3dp"
                android:text="@string/zoom"
                android:textColor="@color/white" />

        </LinearLayout>

        <!--To stop the animation of the image-->
        <Button
            android:id="@+id/stop"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginLeft="30dp"
            android:layout_marginTop="30dp"
            android:layout_marginRight="30dp"
            android:text="@string/stop_animation" />

    </LinearLayout>

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>


```

### MainActivity.java
```java
package com.example.animation;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink, rotate, fade, move, slide, zoom, stop;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}
```
### blink.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
### rotate.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```
### fade.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/accelerate_interpolator">

    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />

</set>
```
### move.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
### slide.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        android:duration="500"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```
### zoom.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```

## OUTPUT
### MainActivity.java
<img width="1917" height="1142" alt="image" src="https://github.com/user-attachments/assets/a5d661e8-4345-46c8-b182-2713b6a79563" />

### activity_main.xml
<img width="1917" height="1140" alt="image" src="https://github.com/user-attachments/assets/1291018a-3b48-4dfa-a5fa-714c5b5563b5" />


### Blink 
<img width="492" height="938" alt="image" src="https://github.com/user-attachments/assets/836eace9-d027-44d7-9245-9ee500245ff6" />

### Rotate
<img width="480" height="921" alt="image" src="https://github.com/user-attachments/assets/71e4318e-0c10-47c7-9074-d739b4e8d279" />

### Fade
<img width="481" height="937" alt="image" src="https://github.com/user-attachments/assets/923c5df9-4fd1-4692-8a86-3db5980d23ed" />

### Move
<img width="496" height="930" alt="image" src="https://github.com/user-attachments/assets/7f4771f3-dab6-4ac1-a22c-af45a09c8320" />

### Slide
<img width="480" height="927" alt="image" src="https://github.com/user-attachments/assets/48bbd3f1-f1c3-429f-8306-191f7a4dd5f4" />
 
### Zoom
<img width="485" height="927" alt="image" src="https://github.com/user-attachments/assets/bdc10fa6-04dc-42d9-8035-cb30cb02d8d2" />


## RESULT

Thus,the experiment Implementation of Animation application using android studio executed successfully.
