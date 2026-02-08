# ALK Zwolle - Website

Website voor het ALK Zwolle Netwerk - Netwerk Aanhoudende Lichamelijke Klachten.

## Over dit project

Dit is een HUGO website voor de ALK onderzoeksgroep in Zwolle. De website biedt informatie over aanhoudende lichamelijke klachten, het onderzoek dat wordt uitgevoerd, en het team van professionals.

## Vereisten

- Hugo Extended versie 0.121.1 of hoger
- Git

## Installatie

1. Clone de repository:
```bash
git clone https://github.com/Aukevanoost/alk-zwolle.git
cd alk-zwolle
```

2. Installeer Hugo (als je dit nog niet hebt):
   - Ga naar https://gohugo.io/installation/
   - Download en installeer de Extended versie voor jouw platform

## Lokale ontwikkeling

Start de Hugo development server:

```bash
hugo server --buildDrafts
```

De website is dan beschikbaar op http://localhost:1313

## Build

Om de website te builden voor productie:

```bash
hugo
```

De gebouwde website wordt geplaatst in de `public/` directory.

## Website structuur

- `/content/` - Alle website content (markdown bestanden)
- `/themes/alk-theme/` - Het custom ALK theme
- `/static/` - Statische bestanden (afbeeldingen, downloads, etc.)
- `/hugo.toml` - Hoofdconfiguratie bestand

## Content bewerken

Om een pagina te bewerken, pas het bijbehorende markdown bestand aan in de `/content/` directory:

- Home pagina: `content/_index.md`
- Over Ons: `content/over-ons.md`
- Onderzoek: `content/onderzoek.md`
- Team: `content/team.md`
- Contact: `content/contact.md`

## Deployment

De website kan gedeployed worden op verschillende platforms:

### GitHub Pages
Voeg een GitHub Actions workflow toe voor automatische deployment.

### Netlify
1. Verbind je GitHub repository met Netlify
2. Build command: `hugo`
3. Publish directory: `public`

### Vercel
1. Importeer het project in Vercel
2. Framework Preset: Hugo
3. Deploy

## Theme aanpassingen

Het custom theme bevindt zich in `/themes/alk-theme/`. Je kunt de volgende bestanden aanpassen:

- Styling: `themes/alk-theme/assets/css/main.css`
- Layouts: `themes/alk-theme/layouts/`
- Kleuren en variabelen: Zie CSS root variabelen in `main.css`

## Licentie

© 2026 ALK Zwolle - Netwerk Aanhoudende Lichamelijke Klachten. Alle rechten voorbehouden.