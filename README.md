# **[ScrollableList](https://developer.android.com/codelabs/basic-android-kotlin-training-recyclerview-scrollable-list?continue=https%3A%2F%2Fdeveloper.android.com%2Fcourses%2Fpathways%2Fandroid-basics-kotlin-unit-2-pathway-3%23codelab-https%3A%2F%2Fdeveloper.android.com%2Fcodelabs%2Fbasic-android-kotlin-training-recyclerview-scrollable-list#0)** 
Learn how to efficiently display a list of text in a RecyclerView and understand its architecture.

<img width="348" src="https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/java/Gif/scrollableview.gif">

## **[activity_main](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/res/layout/activity_main.xml)** 

RecyclerView widget helps you display a list of data.  
RecyclerView comes with built in LayoutManagers. RecyclerView delegates how items are laid out to LayoutManagers.  
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

## **[list_item](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/res/layout/list_item.xml)** 
```xml 
<?xml version="1.0" encoding="utf-8"?>
<com.google.android.material.card.MaterialCardView  xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="8dp">

    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical">
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="194dp"
            android:id="@+id/item_image"
            android:importantForAccessibility="no"
            android:scaleType="centerCrop" />

        <TextView
            android:id="@+id/item_title"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:padding="16dp"
            android:textAppearance="?attr/textAppearanceHeadline6" />

    </LinearLayout>

</com.google.android.material.card.MaterialCardView>
```

## **[Model](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/java/com/codewithkyo/affirmations/model/Affirmation.kt)** 
Use resource annotations to help ensure that the right type of resource ID is passed into a class constructor.  
```kt 
data class Affirmation(
    @StringRes val stringResourceId: Int,
    @DrawableRes val imageResourceId: Int
    )
```

## **[Datasource](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/java/com/codewithkyo/affirmations/data/Datasource.kt)** 
```kt 
class Datasource {

    fun loadAffirmations(): List<Affirmation> {
        return listOf<Affirmation>(
            Affirmation(R.string.affirmation1, R.drawable.image1),
            Affirmation(R.string.affirmation2, R.drawable.image2),
            Affirmation(R.string.affirmation3, R.drawable.image3),
            Affirmation(R.string.affirmation4, R.drawable.image4),
            Affirmation(R.string.affirmation5, R.drawable.image5),
            Affirmation(R.string.affirmation6, R.drawable.image6),
            Affirmation(R.string.affirmation7, R.drawable.image7),
            Affirmation(R.string.affirmation8, R.drawable.image8),
            Affirmation(R.string.affirmation9, R.drawable.image9),
            Affirmation(R.string.affirmation10, R.drawable.image10),
        )
}
```

## **[To implement the adapter](https://github.com/YamamotoDesu/ScrollableList/blob/master/app/src/main/java/com/codewithkyo/affirmations/adapter/ItemAdapter.kt)** 
RecyclerView uses the adapter pattern to adapt and display the data.  
ViewHolder creates and holds the views for RecyclerView.  

Create a custom ViewHolder class that represents a single list item view. Extend from RecyclerView.ViewHolder class.  
Modify the ItemAdapter class to extend from the RecyclerView.Adapter class with the custom ViewHolder class.  
Implement these methods within the adapter: getItemsCount(), onCreateViewHolder(), and onBindViewHolder().  
```kt  
class ItemAdapter(
    private val context: Context,
    private val dataset: List<Affirmation>
) : RecyclerView.Adapter<ItemAdapter.ItemViewHolder>() {

    class ItemViewHolder(private val view: View) : RecyclerView.ViewHolder(view) {
        val textView: TextView = view.findViewById(R.id.item_title)
        val imageView: ImageView = view.findViewById(R.id.item_image)
    }

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ItemViewHolder {
        val adapterLayout = LayoutInflater.from(parent.context)
            .inflate(R.layout.list_item, parent, false)
        return ItemViewHolder(adapterLayout)
    }

    override fun onBindViewHolder(holder: ItemViewHolder, position: Int) {
        val item = dataset[position]
        holder.textView.text = context.resources.getString(item.stringResourceId)
        holder.imageView.setImageResource(item.imageResourceId)
    }

    override fun getItemCount(): Int {
        return dataset.size
    }
}
```
