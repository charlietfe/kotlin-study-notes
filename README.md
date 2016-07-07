#Kotlin notes by theam.

## Overview

This notes are taken in order to serve as a study guide for Kotlin to **theam** developers


## Online resources

* [Kotlin official reference](https://kotlinlang.org/docs/reference/)
* [Kotlin for Android Developers] (https://leanpub.com/kotlin-for-android-developers)
* [Kotlin in Action](https://www.manning.com/books/kotlin-in-action)
* [You can do better with Kotlin by Svetlana Isakova
](https://www.youtube.com/watch?v=bVuhlusXdZ4)

##Main features

* More expresive than Java
* Null Safe (No more fails safe conditions in our code, No more NullPointerException)
* Functional (Uses many concepts of a functional language)
* You can create extension functions to extend any class
* It's highly interoperable, you can use your favourite Java Libraries
* Inmutability (val/var keywords)


###Some examples

**Sample definition of a POJO in Kotlin**

```
	data class Artist(
		var id: Long, 
		var name: String,
		var url: String, 
		var mbid: String) 	
```

`data` keyword provides `toString`, `equals`, `hashCode` and `copy` by default

**Getters and setters**


```
	public class Person {
		var name: String = ""
		
			// We'll need to use field reserved word
			// inside property accesors
		
			get() = field.toUpperCase()
			set(value) {
				field = "Name: $value"
			}
	}
```
**Nullable**

The following code will not compile

```
var name: String
name = null
```

Instead will need to use `?` after type declaration to indicates that a value could be `null`

```
var name: String?
name = null
```
In Java we have tons of code like this *(let's supposed we've an artist object and we want to print his info)*:

```
if (artist != null) {
	return artist.print()
}
```

We could rewrite the above code removing the condition and using a safe method call using `?`

```
return artist?.print()
```


**Extension functions**

Fo exmaple let's extend our Context in Android to provided a nice `Toast`message to our Activities, Fragments or whatever

```
fun Context.toast(message:CharSequence, duration: Int = Toast.LENGTH_SORT) {
	Toast.makeText(this, message, duration).show()
}
``` 

Then in our activities we can call this method directly

```
toast("Hello World!")
toast("Hello World!", Toast.LENGTH_LONG)
```


##Kotlin and Android

