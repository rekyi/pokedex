<div align="center">

# Pokédex

**Browse every Pokémon as a trading card, powered by the PokéAPI**

[![Live](https://img.shields.io/badge/Live-pokedex.rekyi.de-ef5350?style=flat-square)](https://pokedex.rekyi.de)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![PokéAPI](https://img.shields.io/badge/API-PokéAPI-FFCB05?style=flat-square)

[Live demo](https://pokedex.rekyi.de) · [Features](#features) · [Getting started](#getting-started) · [How it works](#how-it-works)

</div>

---

## About

A Pokédex built with plain HTML, CSS and JavaScript – no framework, no build step. Every Pokémon is rendered as a card in the style of the trading card game, loaded on demand from the [PokéAPI](https://pokeapi.co). Clicking a card opens a detailed holographic view with types, evolution stage and attacks.

## Features

- **Trading card design** – each Pokémon type is mapped to one of the eleven card elements (fire, water, grass, …) with matching card frame and type icon. Cards show HP, species, base stats as bars, height and weight.
- **Infinite scroll** – new Pokémon load in batches of 40 as soon as you reach the end of the list, using the `IntersectionObserver` API.
- **Search with suggestions** – type at least three letters to get matching names from all Pokémon. The full name list is only fetched the first time the search field is focused.
- **Detail view** – a native `<dialog>` shows a holographic card with evolution stage (basic, evolved, baby, legendary or mythical), two attacks and all types.
- **Keyboard navigation** – browse through the Pokédex with the arrow keys or the previous / next buttons, close with `Esc`, a click outside or the close button.
- **Robust images** – sprites fall back from official artwork to alternative sprites and finally to a placeholder if an image is missing or fails to load.
- **Alternate forms** – regional and special forms are shown with their form name.
- **Responsive and accessible** – works from small phones to desktop, uses semantic HTML, ARIA labels and respects `prefers-reduced-motion`.
- **Friendly loading screen** – a sleeping Snorlax keeps you company while the first Pokémon load.

## Tech stack

| Area    | Technology                                             |
| ------- | ------------------------------------------------------ |
| Markup  | HTML5 with native `<dialog>`                           |
| Styling | CSS3 (custom properties, grid, media queries)          |
| Logic   | Vanilla JavaScript (ES2020+, `async`/`await`, `fetch`) |
| Data    | [PokéAPI](https://pokeapi.co) REST API                 |

## Getting started

No installation or build step needed.

```bash
git clone https://github.com/rekyi/pokedex.git
cd pokedex
```

Then open `index.html` in your browser. For the smoothest experience, serve the folder with a local web server, for example the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension for VS Code.

An internet connection is required, as all Pokémon data is loaded live from the PokéAPI.

## Project structure

```text
├── index.html
├── script.js              # Entry point, initialises all features
├── style.css              # Header, search and loader
├── favicon.png
└── assets/
    ├── css/
    │   ├── standard.css   # Reset, variables, base styles
    │   ├── grid.css       # Card grid and card layout
    │   └── dialog.css     # Detail view and hologram
    ├── js/
    │   ├── data.js        # API requests and data mapping
    │   ├── grid.js        # Infinite scroll and card rendering
    │   ├── search.js      # Search and suggestions
    │   ├── dialog.js      # Detail view and navigation
    │   └── template.js    # HTML templates
    └── images/
        ├── card_blanks/   # Card frames per element
        └── type_icons/    # Element icons
```

## How it works

1. **Loading** – `grid.js` observes the loading indicator at the end of the list. When it scrolls into view, the next 40 Pokémon are requested from `/pokemon?limit=40&offset=…`.
2. **Mapping** – for every entry, `data.js` fetches the Pokémon and its species in parallel and reduces the API response to the values a card needs. The 18 Pokémon types are mapped to the 11 card elements of the trading card game.
3. **Rendering** – `template.js` turns the prepared data into HTML, and the whole batch is inserted into the grid at once.
4. **Details** – opening a card loads the species data and the first ten moves. Moves with attack power are preferred, so the card shows two meaningful attacks.

## Credits

- Pokémon data and sprites: [PokéAPI](https://pokeapi.co)
- Loading animation: [Pokémon Showdown](https://play.pokemonshowdown.com)

A non-commercial learning project, built to practise asynchronous JavaScript, working with REST APIs and rendering dynamic content. It is not affiliated with Nintendo, Game Freak or The Pokémon Company. Pokémon and all related names are trademarks of their respective owners.

## Contact

[mail@rekyi.de](mailto:mail@rekyi.de) · [GitHub](https://github.com/rekyi) · [Portfolio](https://rekyi.de)
