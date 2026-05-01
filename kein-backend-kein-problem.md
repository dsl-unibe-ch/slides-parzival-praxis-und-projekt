# Kein Backend, kein Problem: <br/>Mit dem Popup-Publisher

<div style="align-self: start;">
Universität Bern, Aktuelle digitale Editionen höfischer
Literatur des Mittelalters, 01.05.2026
</div>
<img src="img/university-of-bern-bern.png" alt="unibe logo" class="bg" style="width: 200px; left:0; top:-10px;"/>


<p class="bg bt-left"><a href="mailto:sebastian.flick@unibe.ch">Sebastian Flick</a></p>
<p class="bg bt-right"><a href="https://dsl.unibe.ch" target="_blank">Data Science Lab</a>, <a href="https://dh.unibe.ch" target="_blank">Digital Humanities</a>, Universität Bern</p>

<style>
  h1 {
    font: 2em var(--font-family) !important;
  }
  .bg {
    position: absolute;
    z-index: -1;
    font-size: 0.7em;
  }
  .bt-left {
    bottom: 0;
    left: 0;
  }
  .bt-right {
    bottom:0;
    right: 0;
  }
</style>

---
Link zu dieser Präsentation:
[https://dsl-unibe-ch.github.io/slides-parzival-praxis-und-projekt/](https://dsl-unibe-ch.github.io/slides-parzival-praxis-und-projekt/)

![qr-code](img/qr.png)

---

## Data Science Lab (DSL)

<img alt="Data Science Lab, Universität Bern" src="img/dsl-site.png"/>

https://dsl.unibe.ch | [support.dsl@unibe.ch](mailto:support.dsl@unibe.ch)

---

## Struktur am DSL

* Team von 5-7 KollegInnen
* Zuständig für den Bereich *Digital Humanities*
* Zurzeit betreuen wir gut 30 Projekte (laufend oder in Planung)

---

## Ressourcen am Leben zu erhalten ist schwierig

|||
|:--:|:--:|
|[![Parzival-Edition (bis 2025)](img/intro-legacy-parzival.png)](https://parzival.unibe.ch/parzdb/index.php) | ![Sicherheitsprobleme aus einem unserer Projekte](img/intro-vulnerabilities.png)|

<style>
  .slide img {
    max-height: 500px;        
    }
</style>
---

## Code-sharing-Plattformen nutzen
<div style="display: flex;">
<div>

- Planung
- Development
- Deployment

<div style="font-size: large;">

CSP: _Code sharing platform_

</div>
</div>



![Code-sharing-Plattformen](img/code-sharing-platforms-2.png)

</div>



---

## Anwendungsgebiete

- Project management
- ~~Data generation~~
- ~~Data management~~
- Data provision
- Data publication

---
  
<div class="footer" data-marked="1">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### ` Project management ` Issues erstellen

|||
|:--:|:--:|
|Problem|Projekte haben eine lange Dauer und mehrere Mitarbeiter.|
|Ansatz|Wir erstellen Issues, denen wir Fälligkeiten und verantwortliche Personen zuweisen.|
|CSP (GitHub)|GitHub **issues**|

---

[![issues in the parzival project](img/project-management-issue.png)](https://github.com/DHBern/presentation_parzival/issues/108)
---
  
<div class="footer" data-marked="4">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### ` Data provision ` Generierung statischer Outputs

|||
|:--:|:--:|
|Problem|Zur Publikation werden spezifische Datenrepräsentationen benötigt. Gleichzeitig sind wir nicht in der Lage, massgefertigte dynamische Systeme langfristig am Laufen zu halten.|
|Ansatz|Vorabgenerierung von Intermediär- und Distributionsformaten für Transkriptionen, Annotationen und andere Projektressourcen.|
|CSP (GitHub)|Bereitstellung der Ergebnisse der Generierungspipelines (XProc, XSLT) als **GitHub Page** („static API“).|

---
  
<div class="footer" data-marked="4">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

|||
|:--:|:--:|
|[![Generation pipeline for static (intermediary) outputs.](img/data-provision-static-api.png)]() | ![Generated outputs ("static API").](img/data-provision-static-api-index.png)|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### ` Data publication ` statisch heisst stetig

|||
|:--:|:--:|
|Problem|Der Betrieb von Backend‑Servern und Datenbanken verursacht hohen Wartungsaufwand, Sicherheitsrisiken und laufende Kosten.|
|Ansatz|Statische Websites sind sicher, schnell und wartungsarm.|
|CSP (GitHub)|GitHub **Actions** und **Pages**|
|Grenzen|Für dynamische Funktionalitäten (Suche, IIIF usw.) nutzen wir universitätsweite Dienste.|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### ` Data publication ` Frontendentwicklung

|||
|:--:|:--:|
|Problem|Obskure Nischen‑Programmierpraktiken erschweren Personalsuche und Onboarding.|
|Ansatz|Der Einsatz moderner JavaScript‑Frameworks und Standards ermöglicht schnelle Entwicklung qualitativ hochwertiger Lösungen.|
|CSP (GitHub)|Statische Website‑Generierung mit GitHub **Actions** (geht weit über SSG‑Tools wie Jekyll hinaus).|

![svelte-machine](img/svelte-machine-desktop.COMO42Ha.avif)

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

### ` Data publication ` Webhosting mit Github Pages

|||
|:--:|:--:|
|Problem|Das Hosten generierter Seiten auf eigenen virtuellen Maschinen ist mit höherem Wartungsaufwand verbunden.|
|Ansatz|Wir nutzen GitHub Pages, um sichere und schnelle statische Websites bereitzustellen.|
|CSP (GitHub)|GitHub **Pages**|

---
  
<div class="footer" data-marked="5">

||||||
|:--:|:--:|:--:|:--:|:--:|
| project management | data generation | data management | data provision | data publication |

</div>

#### Das Frontend _builden_ mit _Actions_

<div style="display: flex; ">

```
build_site:
    runs-on: ubuntu-latest
    services:
      existdb:
        image: existdb/existdb:6.2.0
        ports:
          - 8081:8080
```

```
steps:
- name: Install dependencies
  run: npm ci

- name: start docker
  env:
    EXISTDB_USER: 'admin'
    EXISTDB_SERVER: 'http://127.0.0.1:8081'
  run: npm run installXar

- name: build
  env:
    BASE_PATH: '/${{ github.event.repository.name }}'
    NODE_OPTIONS: '--max_old_space_size=9000'
  run: npm run build
```

</div>
---
## Exkurs: teiPublisher – eine taugliche Fertiglösung?

![TeiPublisher](img/teipb.png)

<style>
  .slide img {
    max-height: 500px;        
    }
</style>
---
Pro:
- Verbreitung, Community (D-A-CH)
- verspricht enorm viele Funktionen
- definiertes TEI-Rendering für viele Elemente/Strukturen

Contra:
- entkoppelt vom Dateisystem; keine direkte Versionierung
- laufende Anwendung erforderlich
- viel Abstraktion, oft hohe Komplexität
- Betrieb bedingt Spezialwissen (z.B. für Backup/Restore, Updates)

---

## Einblick in den Workflow am Beispiel des Parzival
Konzept: <del>teiPublisher</del> → Popup-Publisher
---

TEIPublisher nur für rendering der text views / Transkriptionen

```
fetch(
`${teipb}/parts/${element.handle}.xml/json
?odd=parzival.odd
&view=single
&xpath=//text/body/l[@xml:id=%27${element.handle}_${thirties}.${verse}%27]`)
```

kleingranular möglich durch [XQuery-API (rendered snippets)](https://dhbern.github.io/presentation_parzival/einzelverssynopse/103/07)

---

In der ODD werden nur CSS-Klassen zugewiesen.
```
<elementSpec ident="seg" mode="change">
    <model behaviour="inline" cssClass="glory-initial">
        <param name="subtype" value="Prachtinitiale"/>
    </model>
    <model behaviour="inline" cssClass="initial" useSourceRendition="true">
        <param name="type" value="Initiale"/>
    </model>
</elementSpec>
```
Funktionalität und Design nur im Frontend

---

[Starten der TEI-Publisher-App im build](https://github.com/DHBern/presentation_parzival/blob/main/.github/workflows/main.yml)

```
jobs:
  build_site:
    runs-on: ubuntu-latest
    services:
      existdb:
        image: existdb/existdb:6.2.0
        ports:
          - 8081:8080
    steps:
      - name: Install dependencies
        run: npm ci

      - name: start docker
        env:
          EXISTDB_USER: 'admin'
          EXISTDB_PASS: ''
          EXISTDB_SERVER: 'http://127.0.0.1:8081'
        run: |
          npm run installXar
```
---
[Die Webseite als statische Seite mit SvelteKit _herausrechnen_ (prerender)](https://github.com/DHBern/presentation_parzival/blob/main/src/routes/fassungen/data/%5Bthirties%5D/%2Bserver.js)

```javascript
export async function entries() {
	const entriesArray = Array.from({ length: 827 }, (_, i) => ({ thirties: String(i + 1) }));
	return entriesArray;
}

export const prerender = true;
```
---

![](img/mermaid-diagram-2024-12-04-102140.png)

---
### Resultat
8 GB an HTML, CSS und JS Dateien

(ohne Bilder; diese werden clientseitig direkt vom IIIF-Server der Universitätsbibliothek eingebunden)

[parzival.unibe.ch](https://parzival.unibe.ch/)

---
Vorteile
- solide Grundlage zum Langzeitbetrieb
- inhaltliche Anpassungen sind möglich
- praktisch keine Wartung nötig
- Wartung ohne Domänenkenntnisse möglich
- hohe Performanz
- hohe Zugänglichkeit
- Nachhaltig, da nicht rechenaufwändig
---
Nachteile

- keine Server-seitige Suche möglich (client-seitig schon)
- lange build-Zeiten (~2h)
- keine voll ausgereifte API
---

Danke für Ihre Aufmerksamkeit.
