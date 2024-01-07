---
title: "Swift Optionals"
date: "2022-01-11"
description: "In this post I go over what Optionals are in Swift, and how to access their values."
categories:
    - swift_syntax
---

## What are Optionals in Swift?

Optionals express the fact that a value may or may not exist. If there is a value you will need to unwrap the optional to get at it.

Let’s make a quick Christmas analogy, since it’s only just been.

It’s like an Uncle who loves a joke on Christmas morning. He brings a gift over to the house neatly wrapped. But you don’t truly know if he has wrapped an empty box or if there is a gift inside the box… I guess you’ll have to unwrap it before you can find out!

Under the hood Optionals are just an enum with some syntactic sugar to help us in every day development.

Assuming ‘Gift’ is a type we have created. To declare a type as an optional you would do the following.

```swift
var unclesGift: Gift?
```

Without giving this a value, Swift will default it to nil, meaning there is no value.

Let’s ask the uncle for his gift so we can store it in our variable.

```swift
network.askUncleForGift { gift in
    self.unclesGift = gift
}
```

The signature for the function above looks like this.

```swift
func askUncleForGift(completion: (Gift?) -> ())
```

From this we don’t know if we are definitely going to receive a gift, since it returns an Optional Gift in the completion handler. The only way we can know for sure is by unwrapping the returned gift.

## Unwrapping Optionals

Take the following example, from above.

```swift
var unclesGift: Gift?

network.askUncleForGift { gift in
    self.unclesGift = gift
}
```

The gift object returned from the closure is an optional so we don’t yet know if we have a gift stored in our variable or not.

To find out, we are going to have to use one of a few techniques to unwrap the optional.

First of all we could change the declaration of the variable to the following.

```swift
var unclesGift: Gift!
```

This is implicitly unwrapping the optional. We are effectively saying, we know for certain that when we try to access the value, that a value actually exists; otherwise your app will crash. This is useful predominantly when we know the value will be assigned during object initialisation.

Another mechanism is to force unwrap the variable, which is similar to the above. We would access the variable by appending an exclamation mark after the variable name.

```swift
print(unclesGift!)
```

The problem here is that your app will crash if unclesGift contains no value. Try to avoid force unwrapping optionals for the most part.

A safe way to unwrap an optional is by using an `if let` or a `guard let` statement.

```swift
if let unwrappedUnclesGift = self.unclesGift {
    print(unwrappedUnclesGift)
} else {
    print("Our uncle left us no gift 😔")
}

guard let unwrappedUnclesGift = self.unclesGift else {
    print("Our uncle left us no gift 😔")
    return
}
print(unwrappedUnclesGift)
```

The above mechanisms are safe because we are handling both alternatives, when the variable holds a value, and when it doesn’t. Which mechanism we choose is a matter of logical control flow.

![Swift Language Logo](swift_logo.png)

198
61
80

155