# SEO & RÉFÉRENCEMENT — methodr.io

> **Fichier de suivi permanent.** Consulter avant toute action SEO, mettre à jour après chaque étape réalisée.

---

## État actuel

**Dernière mise à jour :** 17 avril 2026
**Phase :** Fondations techniques — Minimum vital en place
**Prochain jalon :** Vérification Google Search Console

---

## ✅ FAIT — Minimum technique vital

### Fichiers de crawl
- [x] `/robots.txt` déployé — autorise tous les crawlers, pointe vers sitemap
- [x] `/sitemap.xml` déployé — liste accueil + 3 pages légales
- [x] URL de l'image OG accessible : `https://methodr.io/assets/og-image.png`

### Balises meta de base (dans `<head>` de toutes les pages)
- [x] `<title>` unique et descriptif par page
- [x] `<meta name="description">` renseigné
- [x] `<meta name="robots" content="index,follow">` sur les pages publiques
- [x] Open Graph complet (og:title, og:description, og:image, og:url, og:type)
- [x] Favicon cohérent avec la charte

### Données structurées (JSON-LD)
- [x] Schema.org `Organization` — SAS YUEKI, SIREN, adresse, contact
- [x] Schema.org `SoftwareApplication` — Methodr, catégorie, secteur
- [x] Schema.org `WebSite` avec `potentialAction` SearchAction

### Sécurité & performance (bon pour SEO)
- [x] HTTPS actif avec HSTS
- [x] Headers de sécurité (X-Frame-Options, X-Content-Type-Options, Referrer-Policy)
- [x] Site mobile-friendly (responsive)
- [x] Temps de chargement rapide (site statique Netlify CDN)

---

## ⏳ À FAIRE — Phase 1 : Déclaration aux moteurs (à faire par Manu, 10 min)

### Google Search Console
- [ ] Créer un compte sur https://search.google.com/search-console
- [ ] Ajouter la propriété `https://methodr.io`
- [ ] Choisir la méthode de vérification **"Balise HTML"** (la plus simple)
- [ ] Me communiquer le token pour que je l'ajoute au `<head>`
- [ ] Une fois vérifié, soumettre le sitemap : `https://methodr.io/sitemap.xml`
- [ ] **Optionnel mais recommandé** : demander l'indexation manuelle de l'accueil via l'outil "Inspection d'URL"

### Bing Webmaster Tools (complémentaire — optionnel à ce stade)
- [ ] Créer un compte sur https://www.bing.com/webmasters
- [ ] Ajouter le site — Bing accepte d'importer depuis Google Search Console (1 clic)
- [ ] Soumettre le sitemap

### Google Business Profile (si tu accueilles du public à Aix-les-Bains)
- [ ] Créer une fiche SAS YUEKI sur https://www.google.com/business
- [ ] Catégorie : "Éditeur de logiciels" ou "Organisme de formation"
- [ ] Adresse : 725 boulevard Robert Barrier, 73100 Aix-les-Bains
- [ ] Ajouter photos, description, horaires
- [ ] Demander la vérification postale

---

## ⏳ À FAIRE — Phase 2 : Quand le produit est stabilisé (pivot terminé)

### Architecture de pages
- [ ] Convertir le site mono-page en **multi-pages** si nécessaire (une page par persona ou par fonction) — chaque page = une porte d'entrée SEO
- [ ] Mettre en place des **redirections 301** dans `netlify.toml` pour chaque ancienne URL qui change
- [ ] Créer une section blog `/blog/` ou `/ressources/` pour le contenu éditorial

### Contenu éditorial — cœur du SEO long terme
Idées d'articles à fort potentiel (intentions de recherche confirmées sur le métier) :
- [ ] "Comment prendre un mandat exclusif — méthode R0/R1/R2"
- [ ] "Le plan de vente optimal de la prise de mandat vendeur"
- [ ] "R1 découverte vendeur : les 5 phases à ne pas rater"
- [ ] "R2 mandat exclusif : l'ancrage prix qui fait la différence"
- [ ] "Objection 'pas de vitrine' : comment la traiter"
- [ ] "Dashboard commercial immobilier : piloter un réseau sans accompagnement physique"
- [ ] Comparatifs : "Methodr vs CRM immobilier classique"

### Cibles de mots-clés (à valider avec un outil type Google Keyword Planner)
- "prise de mandat exclusif immobilier"
- "méthode prise de mandat"
- "coaching mandataire immobilier"
- "formation R1 R2 immobilier"
- "scoring entretien vendeur"
- "DVF prise de mandat"
- "outil mandataire IAD Safti"

### Netlinking (backlinks)
- [ ] Inscrire methodr.io sur les annuaires pros immobilier (FNAIM, UNIS, Proprietaire.fr, etc.)
- [ ] Articles invités sur blogs immobilier (Immobilier 2.0, Le Mag de l'Immo, Solutions Agence, etc.)
- [ ] Présence sur Product Hunt au lancement public
- [ ] Partenariats réseaux (IAD, Safti, etc.) — échanges de liens

### Tracking & analytics
- [ ] Ajouter un outil d'analytics respectueux RGPD :
  - **Option A** : Plausible (~9€/mois, hébergé EU, pas de cookie banner)
  - **Option B** : Matomo self-hosted (gratuit mais à auto-héberger)
  - **Option C** : Google Analytics 4 (gratuit, nécessite bandeau cookies)
- [ ] Configurer les événements de conversion (inscription bêta, demande devis formation)
- [ ] Créer un dashboard mensuel de suivi

---

## 📋 Règles d'or — à relire AVANT toute évolution du site

### Ce qui NE doit jamais changer sans précaution
1. **Les URLs indexées** — si une URL change, ajouter une redirection 301 dans `netlify.toml` :
   ```toml
   [[redirects]]
     from = "/ancienne-url"
     to = "/nouvelle-url"
     status = 301
   ```
2. **Le domaine principal** — rester sur `methodr.io` (ne pas migrer sauf nécessité absolue)
3. **Les fichiers `/robots.txt` et `/sitemap.xml`** — ne pas supprimer, toujours maintenir à jour

### Ce qui peut évoluer librement
- Le design, la palette, les typos
- Les textes, les titres, les accroches (Google ré-indexe sous 7-14 jours)
- L'image OG
- Les sections internes de la page
- Les positionnements marketing

### En cas de pivot produit
1. Mettre à jour les `<title>` et `<meta description>` avec le nouveau positionnement
2. Actualiser le JSON-LD `SoftwareApplication` (catégorie, description)
3. Régénérer l'image OG si le visuel change
4. Actualiser le contenu du site
5. Dans Google Search Console : faire une "Demande d'indexation" pour accélérer la re-prise en compte
6. Mettre à jour ce fichier `SEO-ROADMAP.md`

---

## 🔧 Checklist technique à surveiller

À vérifier régulièrement (mensuel quand il y a du trafic) :

- [ ] Les pages renvoient toutes un code HTTP 200 (pas de 404 sur les URLs indexées)
- [ ] Le certificat SSL est valide et ne va pas expirer
- [ ] Les performances de chargement restent bonnes (PageSpeed Insights)
- [ ] Aucune erreur dans Google Search Console
- [ ] Le sitemap.xml est à jour (contient toutes les pages publiques)
- [ ] Les données structurées JSON-LD sont valides (tester sur https://search.google.com/test/rich-results)

---

## 📚 Outils utiles (gratuits, à garder sous la main)

| Outil | URL | Usage |
|---|---|---|
| Google Search Console | search.google.com/search-console | Monitoring indexation + trafic organique |
| Bing Webmaster | bing.com/webmasters | Idem pour Bing |
| PageSpeed Insights | pagespeed.web.dev | Tester les perfs |
| Rich Results Test | search.google.com/test/rich-results | Valider le JSON-LD |
| Mobile-Friendly Test | search.google.com/test/mobile-friendly | Vérifier responsive |
| LinkedIn Post Inspector | linkedin.com/post-inspector | Rafraîchir cache OG LinkedIn |
| Facebook Sharing Debugger | developers.facebook.com/tools/debug | Rafraîchir cache OG Facebook/WhatsApp |
| Google Keyword Planner | ads.google.com/intl/fr_fr/home/tools/keyword-planner | Volumes de recherche (nécessite compte Google Ads) |

---

## Journal des modifications SEO

| Date | Action | Résultat |
|---|---|---|
| 17/04/2026 | Mise en place robots.txt + sitemap.xml + JSON-LD sur methodr.io | Fondations techniques OK |
| _à compléter_ | Création Google Search Console | _à documenter_ |
| _à compléter_ | Soumission sitemap à Google | _à documenter_ |
