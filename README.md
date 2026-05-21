# cila-media

Repository pubblico per ospitare asset media (immagini, teaser, post) della pagina **New Cila Club** (Instagram `@cila_club` · Facebook _New Cila Club_).

## A cosa serve

Gli asset qui dentro vengono usati come **URL pubblici** dalle API Meta (Instagram Graph API + Facebook Graph API) per pubblicare/programmare post automaticamente. Meta IG accetta solo immagini con URL pubblico raggiungibile senza autenticazione → repo pubblico = soluzione zero-cost.

**Workflow tipico:**

1. Si produce il teaser/post nello stack di lavoro `~/Progetti/Social Lab/cila-camp/teaser-post-X/`
2. Si esporta il JPEG finale qui in `social-posts/<campagna>/<file>.jpg`
3. `git add` + `commit` + `push`
4. URL pubblico immediato: `https://raw.githubusercontent.com/scerruti-Larry/cila-media/main/social-posts/<campagna>/<file>.jpg`
5. Si passa l'URL all'API Meta tramite MCP (`meta_publish_instagram_photo` con `image_url`)
6. Meta scarica e copia l'immagine sui suoi server — il post resta intatto anche se l'asset qui dovesse essere rimosso

## Struttura

```
cila-media/
├── README.md
├── social-posts/
│   ├── 2026-camp/         # serie 10 post Puzzle Reveal Cila Camp 2026
│   │   ├── teaser-post-01-cinofilia.jpg
│   │   ├── teaser-post-02-padel.jpg
│   │   ├── teaser-post-03-labai.jpg
│   │   └── teaser-post-04-frisbee.jpg
│   └── …                  # campagne future
└── …
```

## Cosa NON va qui

- ❌ File con dati personali di iscritti, lead, contatti
- ❌ Documenti privati cliente (contratti, listini interni, ecc.)
- ❌ Screenshot di dashboard CRM (contengono dati personali genitori)
- ❌ File `.psd`, `.ai`, sorgenti di lavoro pesanti — quelli stanno in `Social Lab/cila-camp/`

Qui SOLO i JPEG finali destinati alla pubblicazione social — cioè materiale **già pubblico per natura**.

## Convenzioni naming

- Snake-case lowercase con prefisso ordinale: `teaser-post-04-frisbee.jpg`
- Estensione `.jpg` (richiesta da Meta IG; PNG non accettato)
- Risoluzione consigliata: 1080×1350 (formato IG portrait 4:5) oppure 2160×2700 per future-proofing

## Storia

Creato 2026-05-21 durante setup pubblicazione automatizzata via Meta MCP. Repo separato da `Social Lab/` (privato, contiene dati di lavoro) per garantire isolamento tra contenuti pubblici e contenuti riservati.
