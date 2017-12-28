# CourtCounter
This is a small App that can be used to keep track of the points in a basketball game. This was made for the Google Developer Challenge 2017-2018 as an assignment to practice with Building Layouts and adding interactivity with Java.

This is how the App behaves:(short video on Youtube)

[![CourtCounter App](http://img.youtube.com/vi/fXy1ms-EImA/0.jpg)](https://youtu.be/fXy1ms-EImA "CourtCounter App")

This is what the UI looks like on my device (Lenovo tablet Lollipop API22)
Portrait

![Udacity CourtCounter App Portrait](https://github.com/elisavetTriant/CourtCounter/blob/master/screenshots/Screenshot_CourtCounter_portrait.png "Udacity CourtCounter App Portrait")

Landscape

![Udacity CourtCounter App Landscape](https://github.com/elisavetTriant/CourtCounter/blob/master/screenshots/Screenshot_CourtCounter_landscape.png  "Udacity CourtCounter App Landscape")

And here is what the layout xml code looks like (file app/src/main/res/layout/activity_main.xml, or https://github.com/elisavetTriant/CourtCounter/blob/Access-Modifiers-Experimentation/app/src/main/res/layout/activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fillViewport="true"
    android:paddingTop="@dimen/root_layout_padding_top"
    android:paddingBottom="@dimen/root_layout_padding_bottom"
    tools:context="com.example.android.courtcounter.MainActivity">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <LinearLayout
                android:layout_weight="1"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:orientation="vertical">

                <TextView
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/TeamAName"
                    android:gravity="center"
                    style="@style/teamsStyle"/>

                <TextView
                    android:id="@+id/team_a_score"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:gravity="center"
                    style="@style/scoreStyle"
                    />

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/_3_points"
                    style="@style/buttonsStyle"
                    android:onClick="addThreeForTeamA"/>

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/_2_points"
                    style="@style/buttonsStyle"
                    android:onClick="addTwoForTeamA"/>

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/free_throw"
                    style="@style/buttonsStyle"
                    android:onClick="addOneForTeamA"/>

            </LinearLayout>
            <View android:layout_width="1dp"
                android:layout_height="match_parent"
                android:background="@android:color/darker_gray"
                />
            <LinearLayout
                android:layout_weight="1"
                android:layout_width="0dp"
                android:layout_height="wrap_content"
                android:orientation="vertical">

                <TextView
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/TeamBName"
                    android:gravity="center"
                    style="@style/teamsStyle" />

                <TextView
                    android:id="@+id/team_b_score"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:gravity="center"
                    style="@style/scoreStyle"/>

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/_3_points"
                    style="@style/buttonsStyle"
                    android:onClick="addThreeForTeamB"/>

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/_2_points"
                    style="@style/buttonsStyle"
                    android:onClick="addTwoForTeamB"/>

                <Button
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="@string/free_throw"
                    style="@style/buttonsStyle"
                    android:onClick="addOneForTeamB"/>

            </LinearLayout>
        </LinearLayout>

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/reset"
            android:onClick="resetGame"
            android:layout_alignParentBottom="true"
            android:layout_centerHorizontal="true"
            android:id="@+id/button"
            />
    </RelativeLayout>
</ScrollView>
```
The design caters for different layout for landscape orientation, file: https://github.com/elisavetTriant/CourtCounter/blob/Access-Modifiers-Experimentation/app/src/main/res/layout-land/activity_main.xml

Don't forget to take a look at the resources folder ( /app/res/values ) and take a look at the code there also. For instance the styles.xml code looks like this now:
```xml
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light">
        <!-- Customize your theme here. -->
        <!-- Primary theme color of the app (sets background color of app bar) -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <!-- Background color of buttons in the app -->
        <item name="colorButtonNormal">@color/colorButtonNormal</item>
    </style>

   <!-- https://developer.android.com/guide/topics/resources/style-resource.html-->
    <style name="scoreStyle">
        <item name="android:padding">@dimen/score_padding</item>
        <item name="android:fontFamily">sans-serif-light</item>
        <item name="android:textColor">@color/colorScores</item>
        <item name="android:textSize">@dimen/score_font_size</item>
        <item name="android:layout_marginTop">@dimen/score_margin_top</item>
        <item name="android:layout_marginBottom">@dimen/score_margin_bottom</item>
    </style>

    <style name="teamsStyle">
        <item name="android:padding">@dimen/team_padding</item>
        <item name="android:fontFamily">sans-serif-medium</item>
        <item name="android:textColor">@color/colorTeams</item>
        <item name="android:textSize">@dimen/team_font_size</item>
    </style>

    <style name="buttonsStyle">
        <item name="android:padding">@dimen/button_padding</item>
        <item name="android:layout_marginBottom">@dimen/button_margin_bottom</item>
        <item name="android:layout_marginTop">@dimen/button_margin_top</item>
        <item name="android:layout_marginRight">@dimen/button_margin_right</item>
        <item name="android:layout_marginLeft">@dimen/button_margin_left</item>
    </style>

</resources>
```
The java code looks like this (app/src/main/java/com/example/android/justjava) or https://github.com/elisavetTriant/CourtCounter/blob/Access-Modifiers-Experimentation/app/src/main/java/com/example/android/courtcounter/MainActivity.java

```java
package com.example.android.courtcounter;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    //Declare and initialize global vars
    private int scoreTeamA = 0;
    private int scoreTeamB = 0;
    //UI objects
    private TextView scoreAView;
    private TextView scoreBView;
    //String constants for keys
    private static final String SCORE_CNT_A = "scoreTeamA";
    private static final String SCORE_CNT_B = "scoreTeamB";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        scoreAView = (TextView) findViewById(R.id.team_a_score);
        scoreBView = (TextView) findViewById(R.id.team_b_score);

        //Display initial global values
        displayForTeamA(scoreTeamA);
        displayForTeamB(scoreTeamB);
    }

    // https://stackoverflow.com/questions/151777/saving-android-activity-state-using-save-instance-state
    //prevent the application from restarting when changing orientation. Saving global vars between activity states.
    @Override
    public void onSaveInstanceState(Bundle savedInstanceState) {
        super.onSaveInstanceState(savedInstanceState);

        // Save UI state changes to the savedInstanceState.
        // This bundle will be passed to onCreate if the process is
        // killed and restarted.
        savedInstanceState.putInt(SCORE_CNT_A, scoreTeamA);
        savedInstanceState.putInt(SCORE_CNT_B, scoreTeamB);
    }

    @Override
    public void onRestoreInstanceState(Bundle savedInstanceState) {
        super.onRestoreInstanceState(savedInstanceState);

        // Restore UI state from the savedInstanceState.
        // This bundle has also been passed to onCreate.
        scoreTeamA = savedInstanceState.getInt(SCORE_CNT_A);
        scoreTeamB = savedInstanceState.getInt(SCORE_CNT_B);

        //Display saved global vars values
        displayForTeamA(scoreTeamA);
        displayForTeamB(scoreTeamB);
    }

    /**
     * Displays the given score for Team A.
     */
    private void displayForTeamA(int score) {
        scoreAView.setText(String.valueOf(score));
    }

    /**
     * Increase the score for Team A by 1 point.
     */
    public void addOneForTeamA(View v) {
        scoreTeamA = scoreTeamA + 1;
        displayForTeamA(scoreTeamA);
    }

    /**
     * Increase the score for Team A by 2 points.
     */
    public void addTwoForTeamA(View v) {
        scoreTeamA = scoreTeamA + 2;
        displayForTeamA(scoreTeamA);
    }

    /**
     * Increase the score for Team A by 3 points.
     */
    public void addThreeForTeamA(View v) {
        scoreTeamA = scoreTeamA + 3;
        displayForTeamA(scoreTeamA);
    }

    /**
     * Displays the given score for Team B.
     */
    private void displayForTeamB(int score) {
        scoreBView.setText(String.valueOf(score));
    }

    /**
     * Increase the score for Team B by 1 point.
     */
    public void addOneForTeamB(View v) {
        scoreTeamB = scoreTeamB + 1;
        displayForTeamB(scoreTeamB);
    }

    /**
     * Increase the score for Team B by 2 points.
     */
    public void addTwoForTeamB(View v) {
        scoreTeamB = scoreTeamB + 2;
        displayForTeamB(scoreTeamB);
    }

    /**
     * Increase the score for Team B by 3 points.
     */
    public void addThreeForTeamB(View v) {
        scoreTeamB = scoreTeamB + 3;
        displayForTeamB(scoreTeamB);
    }

    /**
     * Reset the score, starting a new game.
     */
    public void resetGame(View v) {
        scoreTeamA = 0;
        scoreTeamB = 0;
        displayForTeamA(scoreTeamA);
        displayForTeamB(scoreTeamB);
    }

}
```
