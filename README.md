# **[ScrollableList](https://developer.android.com/codelabs/basic-android-kotlin-training-recyclerview-scrollable-list?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-2-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-recyclerview-scrollable-list#0)** 
Learn how to efficiently display a list of text in a RecyclerView and understand its architecture.

<img width="348" src="https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/java/Gif/scrollableview.gif">


## **[activity_main](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/res/layout/activity_main.xml)** 
```xml 
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recycler_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:scrollbars="vertical"
        app:layoutManager="LinearLayoutManager"
        />
</FrameLayout>
```
