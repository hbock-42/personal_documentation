---
creation date: 2024-05-16 20:40
tags:
  - flutter
  - ui
---
![2024 Google IO Talk](https://www.youtube.com/watch?v=LeKLGzpsz9I)

1. Use SafeArea to stay safe from screen cutouts (notch, keyboard, etc)
2. Use GridView / SliverGridView to adapt you layout to screen size
3. Use Foldables to ease working with foldable screens
4. Layout: 
	-  MediaQuery.sizeOf to get size of screen
	- LayoutBuilder to get size of parent widget
5. Inputs: add supports for different input methods

# Breakpoints
[Material3 recommended breakpoints](https://m3.material.io/foundations/layout/applying-layout/window-size-classes) (you can add your own too):

| Name     | Breakpoint (dp)    | Common devices                                                                                 |
| -------- | ------------------ | ---------------------------------------------------------------------------------------------- |
| Compact  | width < 600        | Phone in portrait                                                                              |
| Medium   | 600 <= width < 840 | Tablet in portait<br>Foldable in portrait (unfolded)                                           |
| Expanded | 840 <= width <1200 | Phone in landscape  <br>Tablet in landscape  <br>Foldable in landscape (unfolded)  <br>Desktop |

# Packages
[responsive_framework -> help building breakpoints](https://pub.dev/packages/responsive_framework)

# Codelab
[Animated responsive layout](https://codelabs.developers.google.com/codelabs/flutter-animated-responsive-layout#0)

# Other
[Overflow menu bar - 11 min](https://www.youtube.com/watch?v=mkxwAKJkc94&list=LL&index=2)
