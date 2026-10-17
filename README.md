Student Task Manager (Android, Java): UI Redesign

A native Android task manager for students. Add, view, edit and delete tasks, stored locally in SQLite. This fork adds a modern UI redesign: new colour palette, Poppins typography, gradient headers, redesigned cards and automatic dark mode.

Show Image

Attribution: this is a fork of Student Task Manager (Android, Java) by Nikhil Rajput (original repository). The original provides the app logic, database layer and layout structure. The changes made in this fork are listed under What this fork adds. The original project states that it is for educational and resume purposes; this fork keeps that intent and credits the original author.

Repository
git clone https://github.com/Hamza-khan53/StudentTask.git
Features
Add new tasks with title and description validation
View all tasks in a scrolling list
Edit existing tasks
Delete tasks with a confirmation dialog
Local storage with SQLite (works offline)
Friendly empty state when there are no tasks
Splash screen on launch
What this fork adds
Area	Change
Colours	Indigo 
#5B5BD6 primary with coral 
#FF7A59 accent on a soft background
Typography	Poppins (Regular, Medium, SemiBold, Bold), bundled with the app
Headers	Gradient toolbar with rounded bottom corners and a subtitle
Task cards	Rounded cards with an accent bar and round tinted Edit / Delete buttons
Empty state	Clipboard illustration with a message
Forms	Fields inside a rounded card, rounded outlines, indigo focus colour
Splash	Gradient background, glowing logo badge, new tagline
Dark mode	Full dark palette that follows the system setting
Dialogs	Rounded delete-confirmation dialog

All view IDs are unchanged, so the original Java code works without modification.

Tech stack
Language: Java
IDE: Android Studio
UI: XML layouts with Material Components, ConstraintLayout, RecyclerView
Database: SQLite via SQLiteOpenHelper
Architecture: Activities + RecyclerView adapter
Min SDK: API 21 (Android 5.0)
Project structure
MainActivity            task list, delete handling
AddTaskActivity         create a task
UpdateTaskActivity      edit a task
SplashActivity          launch screen
TaskAdapter             RecyclerView adapter
DBHelper                SQLite operations
TaskModel               task data class

ui-redesign/
  res/
    layout/             5 redesigned layouts
    drawable/           gradients, icons, empty-state art
    font/               Poppins font files
    values/             colors, themes, styles
    values-night/       dark mode colours
    color/              state-list colours
  preview.png
  FONT_LICENSE_OFL.txt

The *_PSEUDOCODE.java and *_LAYOUT.xml files in the repository root are the source files to copy into an Android Studio project (see below).

How to run (Android Studio)

This repository is not a ready-to-open Android Studio project. Create a blank project and copy the files in:

Create the project: New Project → Empty Activity. Name it Student Task Manager, package com.example.studenttaskmanager, language Java, minimum SDK API 21.
Add dependencies in app/build.gradle, then Sync:
gradle

   implementation 'androidx.appcompat:appcompat:1.6.1'
   implementation 'com.google.android.material:material:1.9.0'
   implementation 'androidx.constraintlayout:constraintlayout:2.1.4'
   implementation 'androidx.cardview:cardview:1.0.0'
   implementation 'androidx.recyclerview:recyclerview:1.3.0'
   
Copy the Java files into app/src/main/java/com/example/studenttaskmanager/, removing _PSEUDOCODE from each name (for example MainActivity_PSEUDOCODE.java becomes MainActivity.java).
Copy the resources: everything inside ui-redesign/res/ goes into app/src/main/res/ (merge folders, overwrite colors.xml and themes.xml).
Register the activities in AndroidManifest.xml. SplashActivity is the launcher and uses Theme.StudentTaskManager.NoActionBar. See AndroidManifest_GUIDE.md for the full example.
Run on an emulator or a USB-connected phone with USB debugging enabled.


Customising the look
Colours: edit res/values/colors.xml (colorPrimary, colorAccent, gradient_start, gradient_end). Dark mode lives in res/values-night/colors.xml.
Font: replace the files in res/font/ and update res/font/poppins.xml.
Text and spacing: adjust the styles in res/values/styles.xml.
Known limitations
Tasks are stored on the device only. There is no sync or account system.
No due dates, priorities or categories yet.
The design preview image is a mock rendered from the same colours and sizes as the XML. Spacing should be checked on a real device or emulator.
Ideas for next steps
Due dates and reminders with notifications
Priority levels shown with the accent bar colour
Task completion toggle with strikethrough
Search and filtering
Room database instead of raw SQLite
Unit and UI tests

