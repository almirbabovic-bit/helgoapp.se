# helgoapp.se

Landningssida för **HelGo** – appen som placerar semesterdagar runt helger och röda dagar.

Statisk sida utan byggsteg. `index.html` innehåller all HTML, CSS och den enda raden
JavaScript (årtalet i sidfoten). Sidan fungerar utan JavaScript.

## Innehåll

```
index.html          hela sidan
img/plan.png|webp   skärmbild av appens planvy
img/kalender.*      skärmbild av appens kalendervy, mars 2027
img/appicon-1024.png, apple-touch-icon.png, icon-512.png
CNAME               helgoapp.se
robots.txt, sitemap.xml
.nojekyll           hindrar Jekyll från att processa filerna
```

## Designkälla

Färger, typografi och mått kommer från appens eget underlag,
`docs/Designunderlag-Helggo.se.md` i repot `almirbabovic-bit/helggo`.
Ändras tokens i appen (`src/theme/tokens.ts`, `src/theme/brand.json`) ska
`:root` i `index.html` uppdateras med. Logotypen är appens egen ikon,
`assets/brand/helgo-appicon-1024.png`, återgiven som inline-SVG med samma geometri.

## Skärmbilderna

Tagna ur appen via webbexporten, i telefonformat 390 × 844 @3x:

```sh
cd <helggo-repot>
npm install
npx expo export --platform web --output-dir dist-web
npx serve dist-web        # eller: python3 -m http.server
```

Fotografera sedan vyerna i 390 px bredd och beskär bort flikraden längst ned.
Byt ut filerna i `img/` och behåll filnamnen.

## Publicera

GitHub Pages, publicering från gren:

1. Pusha innehållet till `main`.
2. Settings → Pages → Source: **Deploy from a branch** → `main` / `/ (root)`.
3. Settings → Pages → Custom domain: `helgoapp.se` → Save.
4. Kryssa i **Enforce HTTPS** när certifikatet är utfärdat.

## DNS hos domänleverantören

Apex-domänen `helgoapp.se`:

| Typ | Namn | Värde |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| AAAA | @ | 2606:50c0:8000::153 |
| AAAA | @ | 2606:50c0:8001::153 |
| AAAA | @ | 2606:50c0:8002::153 |
| AAAA | @ | 2606:50c0:8003::153 |
| CNAME | www | almirbabovic-bit.github.io |

Kontroll: `dig helgoapp.se +noall +answer` och `dig www.helgoapp.se +noall +answer`.

## När appen släpps

I `index.html`, byt ut `<li class="store">` mot `<a class="store" href="...">` på båda
ställena (hjältesektionen och avslutet), ändra `Inte släppt än` till `Ladda ner på` och
ta bort stycket `Appen är under utveckling…`.
