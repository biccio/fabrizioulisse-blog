---
title: Hugo, un tema e un blog
summary: Dopo tanti CMS installati, usati, modificati e forzati, volevo un framework leggero ed efficace per i miei progetti personali. E ho conosciuto Hugo.
description: "Perché ho scelto Hugo come static site generator per i progetti personali, come si installa e il tema Kraft Masonry creato per questo blog."
date: 2026-05-28
lastmod: 2026-05-28
categories:
  - tech
tags:
  - hugo
  - web
  - dev
  - cms
  - blog
featured: true
schema:
  type: "BlogPosting"
  headline: "Hugo, un tema e un blog"
  inLanguage: "it-IT"
  articleSection: "tech"
  wordCount: 546
  mainEntityOfPage: "# DA INSERIRE"
  author:
    name: "Fabrizio Ulisse"
    url: "https://fabrizioulisse.it/about/"
  publisher:
    name: "Fabrizio Ulisse [un blog]"
    url: "https://fabrizioulisse.it"
  about:
    - type: "SoftwareApplication"
      name: "Hugo"
      sameAs: "https://gohugo.io/"
  mentions:
    - { type: "SoftwareApplication", name: "WordPress",  sameAs: "https://wordpress.org/" }
    - { type: "SoftwareApplication", name: "Strapi",     sameAs: "https://strapi.io/" }
    - { type: "SoftwareApplication", name: "Decap CMS",  sameAs: "https://decapcms.org/" }
    - { type: "SoftwareApplication", name: "Kraft Masonry (tema Hugo)", sameAs: "https://github.com/biccio/hugo-kraft-masonry" }
    - { type: "ComputerLanguage",    name: "Go",         sameAs: "https://go.dev/" }
    - { type: "Organization",        name: "Netlify",    sameAs: "https://www.netlify.com/" }
---
Ho cominciato a frequentare CMS per lavoro e passatempo più di vent'anni fa, quando iniziavano ad uscire i primi sistemi hosted come [Blogger](https://www.blogger.com/about/?bpli=1) (o [Splinder](https://it.wikipedia.org/wiki/Splinder) per chi se lo ricorda) o self-hosted come [Movable Type](https://www.movabletype.com/) (che esiste ancora, ho appena scoperto!) o [Wordpress](https://wordpress.org/) ai suoi albori e per molti anni a seguire, fino ai moderni headless come [Strapi](https://strapi.io/) (che uso abitualmente per lavoro) o [Payload](https://payloadcms.com/). Per i miei progetti personali ero però alla ricerca di una soluzione più light, rispetto a come sono diventati questi CMS, ormai stracarichi di complessità e di feature, ingordi di manutenzione e perennemente a rischio virus, spam o collassi da plugin scritti male. Mi sono quindi orientato verso soluzioni [SSG](https://developer.mozilla.org/en-US/docs/Glossary/SSG) (static site generation), tra le quali la più interessante mi è sembrata [Hugo](https://gohugo.io/)

## Cos'è Hugo
Hugo è un framework per la generazione statica di siti web, molto leggero e funzionale, scritto in [Go](https://go.dev/). Si basa su temi (relativamente semplici da implementare), e nel suo essere leggero ed efficiente è in realtà molto potente, e consente un notevole livello di personalizzazione dei layout.
Sostanzialmente funziona così: si scrivono articoli e post in formato markdown, e si lancia una build che genererà le pagine statiche del sito sulla base delle indicazioni di layout presenti nel tema scelto, e di un file di configurazione in formato [YAML](https://it.wikipedia.org/wiki/YAML) o [TOML](https://it.wikipedia.org/wiki/TOML) , che si incarica di fornire al motore di build variabili di contenuto o di funzione. L'uso più classico prevede build in locale per i test, e deploy su [Netlify](http://netlify.com/) o simili piattaforme cloud (che si prendono in carico anche la gestione della build, a partire da contenuto ospitato su repo Github). 
## Come si installa Hugo
Perché sia possibile farlo funzionare in locale, occorre fare poche cose:

Installare Hugo (per Mac e Linux si fa presto con `brew`):
```
brew install hugo
```
Creare un nuovo sito:
```
hugo new site sitename
```
Posizionarci sulla directory dove abbiamo creato il sito
```
cd site
```
Installare un tema come `submodule` da Github (qui indichiamo [il tema in uso qui](https://github.com/biccio/hugo-kraft-masonry) sul blog)
```
git submodule add https://github.com/biccio/hugo-kraft-masonry.git themes/hugo-kraft-masonry
```
Inserirne il riferimento nel file di confgurazione `hugo.toml`
```
echo "theme = ‘hugo-kraft-masonry’” >> hugo.toml
```
Per lanciare il sito in locale poi basterà poi questo comando
```
hugo server
```
e potrete vedere il sito funzionante su `localhost` porta `1313`. Semplicissimo.

## Il tema Kraft Masonry
Ho già un'installazione attiva di Hugo per il mio sito di viaggi in bici [Ciclogravelista](https://ciclogravelista.com/), per il quale uso l'ottimo tema [Hextra](https://github.com/imfing/hextra), ma per riavviare questo mio blog personale (che tra alti e bassi esiste dal 2001!) avevo voglia di farmi un tema da solo, basandolo sul principio della griglia [Masonry](https://masonry.desandro.com/). Così ho lavorato di vibe coding con Claude, e il risultato è [questo tema](https://github.com/biccio/hugo-kraft-masonry), creato in un'oretta circa, su cui ho costruito il blog, e che ho deciso di mettere a disposizione di chi volesse usarlo per i propri siti.

## Limiti di Hugo (e degli SSG in generale)
Il problema più grande in realtà di tutti i SSG e proprio l'assenza di un CMS, e questo rende meno facile manutenere un sito così realizzato, per una persona meno esperta o senza il proprio computer disponibile per fare i `commit` su Github. A questo problema si può ovviare installando [Decap](https://decapcms.org/docs/hugo/), un CMS open source installabile in qualunque sito i cui contenuti sono `git` based. A me non convince ancora molto, ma se evolvesse nella giusta direzione potrebbe contribuire a trasformare il paradigma SSG in un'ottima alternativa a un CMS tradizionale per utenti meno esperti.