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
ArrayAdapter adapter = new ArrayAdapter<>(Context, dropdown layout, String array/ArrayList of options);

To give the ACTV an array or ArrayList of options, we must create an ArrayAdapter. 
We then set this as our ACTV's adapter using the following method:

setAdapter(adapter);

The ACTV will begin showing autocomplete options after a certain number of characters

