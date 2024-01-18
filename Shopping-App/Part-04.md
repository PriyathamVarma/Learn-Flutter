[<-- Part-03.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-03.md) | [Part 05 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-05.md)

## Fetching and transforming data

```mermaid

graph TD

A[lib] --> B[src]
B --> C[ui]
C --> D[screens]
C --> E[common]
C --> F[widgets]
B --> G[models]
B --> H[providers]
B --> I[Data]
I --> J[groceries_data.dart]
G --> K[groceries_model.dart]
H --> L[groceries_provider.dart]
E --> M[appbar_widget.dart]
D --> N[groceries_screen.dart]
E --> O[SideDrawerWidget.dart]


```

```dart
final url = Uri.https(
       "<link>.com",
      'shopping-list.json');

    void fetchData() async {
      //var groceriesDataFromFirebase = await http.get(url).then((value) => null);
    }

```



[<-- Part-03.md](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-03.md) | [Part 05 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Shopping-App/Part-05.md)
