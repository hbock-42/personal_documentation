---
title: Destructuring and type promotion
creation date: 2024-03-28 14:54
tags:
  - documentation
  - dart
cssclasses:
  - md-full-width
---
# Type promotion
[Type promotion](https://dart.dev/tools/non-promotion-reasons#:~:text=Type%20promotion%20occurs%20when%20flow,causing%20type%20promotion%20to%20fail.) is the action of verifying conditions on a variable to promote it to a stricter type.
Exemple of promoting a nullable string:
```dart 
int barista(String? name) {  
  // int nameLength = name.length; <== does not compile: we cannot use .length on  
  // nullable string (String?) because .length does not exists 
  // on null
  if (name != null) {  
    return name.length; // <== even tho name is a nullable string (String?)  
    // we can use .length inside this scope because it has been promoted    // to String.  }  
  return 0;  
}
```

> [!information] Currently only works for local variable
> 
> You can save nested variables you want to promote inside a local variable as a workaround

# Destructuring and type promotion exemple
```dart
Upgrader(
	minAppVersion: switch (remoteConfigState) {
		RemoteConfigLoadedState(remoteConfig: RemoteConfig(:final Some<String> minAppVersionOption)) => minAppVersionOption.value,
		RemoteConfigErrorState() || RemoteConfigLoadingState() || RemoteConfigLoadedState() => null,
	},
```
