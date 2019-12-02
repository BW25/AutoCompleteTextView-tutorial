# AutoCompleteTextView tutorial
 A tutorial and demo app for the Android AutoCompleteTextView 

## Introduction
The AutoCompleteTextView (ACTV) is a variant on the standard TextView used to display text to the screen.

An ACTV is editable, and when text is typed into it, it displays autocomplete options as a dropdown menu.

This can serve to guide users when a known input is expected, but offers more flexibility than a standard dropdown menu.

## History
The ACTV has been around since API 1, meaning it has existed since the original Android implementation!

It is included in the	android.widget package.


## Inheritance
As it extends EditText, it's inheritance tree is as follows:

java.lang.Object -> android.view.View -> android.widget.TextView -> android.widget.EditText -> android.widget.AutoCompleteTextView

It also extends the Filter.FilterListener.

This allows it to filter the input to determine which of the autocomplete options to display


## Major features

### ArrayAdapter adapter = new ArrayAdapter<>(Context, dropdown layout, String array/ArrayList of options);

To give the ACTV an array or ArrayList of options, we must create an ArrayAdapter. 
The ArrayAdapter takes an array or ArrayList of Strings, which will serve as the autocomplete options.
We then set this as our ACTV's adapter using the following method:

### setAdapter(adapter);

The ACTV will begin showing autocomplete options after a certain number of characters.
The number of characters is set using the following method, which takes an integer as an argument:

### setThreshold(integer);

### Updating the autocomplete options

The ACTV uses a preset list of options. However, this list can be manually changed.
This is done by altering the list in code, and then recreating the adapter and once again setting it as the ACTV's adapter. (See start of the section.)
For this purpose, an ArrayList may be easier to edit and append to to add additional options.
Alternatively, an entirely new list of options could be added.
If it is desired to retain the options, it may be necessary to use SharedPreferences.
https://developer.android.com/reference/android/content/SharedPreferences

Please note that the autocomplete options may have multiple of the same option. This can be prevented by checking the list for a String before adding it, to prevent duplicates.

Please see the demo code to see this feature in action.



## Notes
Please note that the drop down menu will be the same width as the AutoCompleteTextView.
If you set the width to "wrap_content", the width of the drop down menu may make the text too small to read.
I recommend setting it to a larger width manually, or placing it in a larger view and setting it to match_parent.

Options are considered a match based on the first letter of any word in the string, not just the first word


## References

Official Android documentation:
https://developer.android.com/reference/android/widget/AutoCompleteTextView.html#getThreshold()

