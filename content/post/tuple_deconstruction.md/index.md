---
title: "Swift Tuple Deconstruction"
date: "2022-01-10"
description: "In this post I go over a better way to access all of the values in a Tuple."
categories:
    - swift_syntax
comments: true
---

Tuple Deconstruction is quite a great way to access the contents of a Tuple, which is often overlooked.

Let’s create a tuple representing my name and age.

```swift
let myDetails: (name: String, surname: String, age: Int) = ("Connor", "Black", 26)
```

The typical way to access these values would be the following.

```swift
let name = myDetails.name
let surname = myDetails.surname
let age = myDetails.age
```

This is of course, completely valid. But we can certainly do better! Time to give Tuple Deconstruction a go!

```swift
let (name, surname, age) = myDetails
```

Yep… That’s it! We’ve saved 2 lines of code, and in my opinion this is more readable.

![Swift Language Logo](swift_logo.png)