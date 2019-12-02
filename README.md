# AutoCompleteTextView tutorial
 A tutorial and demo app for the Android AutoCompleteTextView

## Introduction
The AutoCompleteTextView (ACTV) is a variant on the standard TextView used to display text to the screen.

An ACTV is editable, and when text is typed into it, it displays autocomplete options as a dropdown menu.

This can serve to guide users when a known input is expected, but offers more flexibility than a standard dropdown menu.

Throughout this tutorial, when you see mText, we are referring to an ACTV object created in code.

## History
The ACTV has been around since API 1, meaning it has existed since the original Android implementation!

It is included in the	android.widget package.


## Inheritance
As it extends EditText, it's inheritance tree is as follows:

java.lang.Object -> android.view.View -> android.widget.TextView -> android.widget.EditText -> android.widget.AutoCompleteTextView

It also extends the Filter.FilterListener.

This allows it to filter the input to determine which of the autocomplete options to display


## Creating and using the AutoCompleteTextView

#### 1. Place an AutoCompleteTextView in the layout resource file.

``<AutoCompleteTextView
android:id="@+id/autoCompleteTextView"
android:layout_width="match_parent"
android:layout_height="wrap_content" />``

Please note that the drop down menu will be the same width as the AutoCompleteTextView.
If you set the width to "wrap_content", the width of the drop down menu may make the text too small to read.
I recommend setting it to a larger width manually, or placing it in a larger view and setting it to match_parent.

#### 2. Add the necessary imports

Go to the activity that is using the ACTV, and add the necessary import to use the class:

``import android.widget.AutoCompleteTextView;``

#### 3. Create a variable to represent the ACTV

``AutoCompleteTextView mText;``

This variable can be a class variable if you need to access the ACTV outside of onCreate(). Otherwise, this declaration should go in onCreate() along with the next step.

#### 4. Assign the ACTV from the layout file to a variable in code

This can be done as with any View using the findViewById() method.

``mText = findViewById(R.id.autoCompleteTextView);``

#### 5. Create a list of autocomplete options

An ACTV takes an array or ArrayList of Strings. These strings serve as its autocomplete options. Create an array or ArrayList with your desired autocomplete options. Here is a sample one of foods, but you should create your own as needed. This 

``private static String[] DEFAULT_OPTIONS = new String[] {"Apples", "Brioche", "Canned Tuna", "Donuts", "Eclairs", "Fish", "Gummi Worms", "Halibut", "Intestines",
"Jellybeans", "Kelp", "Lozenges", "Milk", "Nougat", "Olives", "People", "Quesedillas", "Rabbit", "Snake hearts",
"Toffee", "Underwear", "Vuvuzelas", "Worms", "Xanthum gum", "Yams", "Zebras"};``

(optional)
I chose to use an ArrayList, which lets me easily add or remove options later. I created the ArrayList from my array of default options using this code:

``ArrayList<String> options = new ArrayList<>(Arrays.asList(DEFAULT_OPTIONS));``

#### 6. Create an ArrayAdapter to allow the ACTV to use the array/ArrayList

This method takes three arguments: the Context, the layout, and your array or ArrayList of options

``ArrayAdapter adapter = new ArrayAdapter<>(this, android.R.layout.simple_dropdown_item_1line, options);
``

#### 7. Attach the adapter to your ACTV. 

``mText.setAdapter(adapter);``

Now your ACTV will use your autocomplete options!


## Updating the autocomplete options

The ACTV uses a preset list of options. However, this list can be manually changed.
This is done by altering the list in code, and then recreating the adapter and once again setting it as the ACTV's adapter. (Repeating steps 6 and 7)
For this purpose, an ArrayList may be easier to edit and append to to add additional options.
Alternatively, an entirely new list of options could be added.
If it is desired to retain the options, it may be necessary to use SharedPreferences.
https://developer.android.com/reference/android/content/SharedPreferences

Please note that the autocomplete options may have multiple of the same option. This can be prevented by checking the list for a String before adding it, to prevent duplicates.

Please see the demo code to see this feature in action.

## Additional features

The ACTV will begin showing autocomplete options after a certain number of characters.
The number of characters is set using the following method, which takes an integer as an argument:

``mText.setThreshold(integer);``

This may also be set in the xml layout file using:

``android:completionThreshold``

### Inherited features

As the ACTV extends TextView and EditText, it has inherited many of its methods and features. 

The text value of the ACTV can be retreived using ``mText.getText()``

The text can be set using ``mText.setText(CharSequence text, TextView.BufferType type);``

Alternatively, additional text can be appended using ``mText.append(CharSequence text)``

The length of the text currently in the ACTV can be retrieved as an integer using``mText.length()``

The ACTV may also display a hint when it is empty, which can be set with ``mText.setHint(CharSequence hint)``

## Notes

Options are considered a match based on the first letter of any word in the string, not just the first word

## References

Official Android documentation:
https://developer.android.com/reference/android/widget/AutoCompleteTextView.html#getThreshold()

An additional tutorial:
https://www.javatpoint.com/android-autocompletetextview-example
