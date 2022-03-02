# Éval Angular M1 CP IL - 02/03/2022

## Livrable attendu

* Idéalement un dépôt sur GitHub
* Application avec deux pages : accueil (liste de films) et détails (détails d'un film)
* Bonus :

    * afficher des commentaires dans la page de détails (voir _endpoints API_ &rarr; _détails d'un film_ _noter et commenter un film_)
    * afficher un formulaire pour poster un commentaire depuis la page de détails (voir _endpoints API_ &rarr; _noter et commenter un film_)

## Méthodologie

* Commencez par réfléchir aux composants dont vous aurez besoin pour chaque page
* Vous pouvez utiliser des données "en dur" pour commencer, au lieu de faire directement des appels API
* Vous devrez implémenter la navigation (voir ressources / Doc Angular)
* Une fois que vous avez des pages "statiques" avec les données en dur, vous pouvez remplacer ces données par celles issues de "vraies" données, obtenues par requêtes HTTP.

## Ressources

### Doc Angular

* [Display a list](https://angular.io/tutorial/toh-pt2) (issu du tutoriel "Tour of Heroes")
* [Add navigation with routing](https://angular.io/tutorial/toh-pt5)
* [Get data from a server](https://angular.io/tutorial/toh-pt6) (idem... passez la partie "Simulate a data server" car vous avez une vraie API à disposition)

### Template HTML

Un template est fourni mais il n'est **pas obligatoire** (du tout) de l'utiliser.

Il vise juste à avoir une base pour démarrer, pour celles et ceux qui ne veulent pas perdre trop de temps sur du CSS.


* [ZIP du template à télécharger](https://github.com/bhubr/movies-app-html-template/archive/refs/heads/master.zip)
* [Repo du template (mais utilisez le Zip c'est mieux)](https://github.com/bhubr/movies-app-html-template)

**D'autres possibilités existent** : 

* Adapter un autre template HTML (il en existe de nombreux en cherchant "movie library template")
* Utiliser une bibliothèque de composants comme [Angular Material](https://material.angular.io/), [Ng Bootstrap](https://ng-bootstrap.github.io/#/home), etc.

### Cours

Cours dont les slides des TD : https://m1cp.bhu.ovh/

## Endpoints API

### Liste de tous les films

À utiliser pour "peupler" la page d'accueil

URL : <https://movie-api.benoithubert.me/movies/>

Renvoie les données de base d'un film, dont :

* `id`
* `title`
* `poster_path` &rarr; image du film

Extrait (ici avec 2 films, l'API en renvoyant 60) :

```json
[
  {
    "adult": false,
    "genre_ids": [28, 12, 878],
    "id": 634649,
    "original_language": "en",
    "original_title": "Spider-Man: No Way Home",
    "overview": "Peter Parker is unmasked and no longer able to separate his normal life from the high-stakes of being a super-hero. When he asks for help from Doctor Strange the stakes become even more dangerous, forcing him to discover what it truly means to be Spider-Man.",
    "popularity": 5944.171,
    "release_date": "2021-12-15",
    "title": "Spider-Man: No Way Home",
    "video": false,
    "vote_average": 8.3,
    "vote_count": 8569,
    "poster_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/1g0dhYtq4irTY1GPXvft6k4YLjm.jpg",
    "backdrop_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/iQFcwSGbZXMkeyKrxbPnwnRo5fl.jpg"
  },
  {
    "adult": false,
    "genre_ids": [16, 35, 10751, 14],
    "id": 568124,
    "original_language": "en",
    "original_title": "Encanto",
    "overview": "The tale of an extraordinary family, the Madrigals, who live hidden in the mountains of Colombia, in a magical house, in a vibrant town, in a wondrous, charmed place called an Encanto. The magic of the Encanto has blessed every child in the family with a unique gift from super strength to the power to heal—every child except one, Mirabel. But when she discovers that the magic surrounding the Encanto is in danger, Mirabel decides that she, the only ordinary Madrigal, might just be her exceptional family's last hope.",
    "popularity": 2872.237,
    "release_date": "2021-11-24",
    "title": "Encanto",
    "video": false,
    "vote_average": 7.7,
    "vote_count": 4850,
    "poster_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/4j0PNHkMr5ax3IA8tjtxcmPU3QT.jpg",
    "backdrop_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/3G1Q5xF40HkUBJXxt2DQgQzKTp5.jpg"
  }
]
```

### Détails d'un film

À utiliser pour "peupler" la page de détails

URL : <https://movie-api.benoithubert.me/movies/:id> (remplacer `:id` par l'id d'un film)

Renvoie les données détaillées d'un film, dont :

* les données précédentes
* la durée dans `runtime`
* l'année (et les mois et jour) dans `release_date`
* la liste des genres dans le tableau `genres`
* la liste des studios dans le tableau `production_companies`
* un tableau `comments` (vide au début) **qui pourra être utilisé si vous avez le temps de faire le "bonus"**

Données renvoyées [pour le film `634649`](https://movie-api.benoithubert.me/movies/634649) :

```json
{
  "adult": false,
  "backdrop_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/iQFcwSGbZXMkeyKrxbPnwnRo5fl.jpg",
  "belongs_to_collection": {
    "id": 531241,
    "name": "Spider-Man (Avengers) Collection",
    "poster_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/nogV4th2P5QWYvQIMiWHj4CFLU9.jpg",
    "backdrop_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/AvnqpRwlEaYNVL6wzC4RN94EdSd.jpg"
  },
  "budget": 200000000,
  "genres": [
    { "id": 28, "name": "Action" },
    { "id": 12, "name": "Adventure" },
    { "id": 878, "name": "Science Fiction" }
  ],
  "homepage": "https://www.spidermannowayhome.movie",
  "id": 634649,
  "imdb_id": "tt10872600",
  "original_language": "en",
  "original_title": "Spider-Man: No Way Home",
  "overview": "Peter Parker is unmasked and no longer able to separate his normal life from the high-stakes of being a super-hero. When he asks for help from Doctor Strange the stakes become even more dangerous, forcing him to discover what it truly means to be Spider-Man.",
  "popularity": 5944.171,
  "poster_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/1g0dhYtq4irTY1GPXvft6k4YLjm.jpg",
  "production_companies": [
    {
      "id": 420,
      "logo_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/hUzeosd33nzE5MCNsZxCGEKTXaQ.png",
      "name": "Marvel Studios",
      "origin_country": "US"
    },
    {
      "id": 84041,
      "logo_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/nw4kyc29QRpNtFbdsBHkRSFavvt.png",
      "name": "Pascal Pictures",
      "origin_country": "US"
    },
    {
      "id": 5,
      "logo_path": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/71BqEFAF4V3qjjMPCpLuyJFB9A.png",
      "name": "Columbia Pictures",
      "origin_country": "US"
    }
  ],
  "production_countries": [
    { "iso_3166_1": "US", "name": "United States of America" }
  ],
  "release_date": "2021-12-15",
  "revenue": 1832000000,
  "runtime": 148,
  "spoken_languages": [
    { "english_name": "English", "iso_639_1": "en", "name": "English" },
    { "english_name": "Tagalog", "iso_639_1": "tl", "name": "" }
  ],
  "status": "Released",
  "tagline": "The Multiverse unleashed.",
  "title": "Spider-Man: No Way Home",
  "video": false,
  "vote_average": 8.3,
  "vote_count": 8574,
  "comments": []
}
```

### _Noter et commenter un film_

À utiliser pour envoyer une note et un commentaire vers l'API (récupérés dans le tableau `comments` du endpoint précédent)

URL **accessible en POST** : <https://movie-api.benoithubert.me/movies/:id/comments> (remplacer `:id` par l'id d'un film)

Format des données à envoyer :

* Un champ `rating` numérique inférieur ou égal à 10
* Un champ `text` avec le commentaire

```json
{
  "rating": "8",
  "text": "Quite the scary movie too"
}
```
