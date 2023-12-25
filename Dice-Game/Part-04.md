[<- Part 03: Variables, Functions](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md) |

<hr/>

## Using buttons and multiple constructor functions

<details>

<summary>  Buttons in Flutter </summary>

Flutter offers a variety of buttons to enhance user interaction in your apps.

**Types of Buttons**

- TextButton: A plain button with text content. Ideal for secondary actions or dialogs.

- ElevatedButton: A raised button with a shadow, often used for primary actions.

- OutlinedButton: A button with a border outline and no fill, suitable for subtle actions.

- IconButton: A compact button displaying only an icon.

- FloatingActionButton: A circular button, typically placed near the bottom corner for primary actions.

**Customizing Buttons**

- Styling: Modify button appearance using the style parameter (color, padding, shadow, etc.).

- Theme: Apply global styles using button themes (TextButtonTheme, ElevatedButtonTheme, etc.).

- On Press: Define the button's behavior using the onPressed callback.


> [!TIP]
> Additional Considerations

> Accessibility: Ensure proper text contrast and labels for screen readers.

> State Management: Update button appearance based on user interaction and app state.

> Button Themes: Create custom themes for consistent button styles throughout your app.




**Sample Code**


```dart
// Text Button
TextButton(
  onPressed: () => print('Clicked!'),
  child: Text('Click Me'),
),

// Elevated Button
ElevatedButton(
  onPressed: () => print('Do something important'),
  child: Text('Start Now'),
),

// Floating Action Button
FloatingActionButton(
  onPressed: () => Navigator.pushNamed(context, '/'),
  child: Icon(Icons.add),
),
```
  
</details>


<hr/>

[<- Part 03: Variables, Functions](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Dice-Game/Part-03.md) |

