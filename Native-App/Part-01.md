[<-- Readme](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Native-App/README.md) | [Part 02 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Native-App/Part-02.md)


```mermaid


graph TD

A[src] --> B[ui]
B --> C[screens]
B --> D[common]
B --> E[widgets]
E --> F[image_input.dart]
C --> G[add_place_screen.dart]
C --> H[place_details_screen.dart]
C --> I[places_screen.dart]
E --> J[places_list_screen.dart]
A --> K[models]
K --> L[place.dart]
A --> M[providers]
M --> N[user_places.dart]


```

## Previewing the picked Image

> places_list_screen.dart

<details>
  <summary>Code</summary>

```dart

import 'package:flutter/material.dart';

import 'package:native_app/src/models/place.dart';
import 'package:native_app/src/ui/screens/place_details_screen.dart';

class PlacesList extends StatelessWidget {
  const PlacesList({super.key, required this.places});

  final List<Place> places;

  @override
  Widget build(BuildContext context) {
    if (places.isEmpty) {
      return Center(
        child: Text(
          'No places added yet',
          style: Theme.of(context).textTheme.bodyLarge!.copyWith(
                color: Theme.of(context).colorScheme.onBackground,
              ),
        ),
      );
    }

    return ListView.builder(
      itemCount: places.length,
      itemBuilder: (ctx, index) => ListTile(
        leading: CircleAvatar(
          radius: 26,
          backgroundImage: FileImage(places[index].image),
        ),
        title: Text(
          places[index].title,
          style: Theme.of(context).textTheme.titleMedium!.copyWith(
                color: Theme.of(context).colorScheme.onBackground,
              ),
        ),
        onTap: () {
          Navigator.of(context).push(
            MaterialPageRoute(
              builder: (ctx) => PlaceDetailScreen(place: places[index]),
            ),
          );
        },
      ),
    );
  }
}


```
  
</details>

## Adding the location package & starting with get location


<details>
  <summary>Code</summary>

```dart



```
  
</details>




<details>
  <summary>Code</summary>

```dart


```
  
</details>









[<-- Readme](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Native-App/README.md) | [Part 02 -->](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Native-App/Part-02.md)
