# SEO & RÉFÉRENCEMENT — methodr.io

> **Fichier de suivi permanent.** Consulter avant toute action SEO, mettre à jour après chaque étape réalisée.

---

## État actuel

**Dernière mise à jour :** 19 avril 2026
**Phase :** Fondations techniques COMPLÈTES + vérification Google validée + accueil indexé
**Prochain jalon :** Soumettre sitemap.xml dans Google Search Console (2 min) → indexation des 3 pages légales

---

## ✅ AUDIT DU 19/04/2026 — TOUT LE MINIMUM VITAL EST EN PLACE

### Fichiers de crawl — vérifiés en production

| Fichier | URL | État |
|---|---|---|
| robots.txt | https://methodr.io/robots.txt | ✅ HTTP 200 — autorise tous les crawlers, référence le sitemap |
| sitemap.xml | https://methodr.io/sitemap.xml | ✅ HTTP 200 — 4 URLs listées (accueil + 3 pages légales) |
| Image OG | https://methodr.io/assets/og-image.png | ✅ HTTP 200 — 60 KB, charte v3 indigo |

### Balises `<head>` de la page d'accueil — vérifiées

| Balise | État | Valeur |
|---|---|---|
| `<title>` | ✅ | "Methodr — Intelligence commerciale terrain pour l'immobilier" |
| `meta description` | ✅ | Description riche avec mots-clés métier |
| `meta robots` | ✅ | `index, follow, max-image-preview:large` |
| `link canonical` | ✅ | `https://methodr.io/` |
| `html lang` | ✅ | `fr` |
| `meta author` | ✅ | `SAS YUEKI` |
| Open Graph | ✅ | Complet : og:title, og:description, og:url, og:image, og:image:width, og:image:height, og:site_name, og:locale, og:type |
| Twitter Card | ✅ | `summary_large_image` + title + description + image |
| Favicon | ✅ | SVG intégré, cohérent charte v3 (fond noir, "M" blanc) |

### Données structurées JSON-LD — 3 entités schema.org déclarées

| Type | Détails |
|---|---|
| `Organization` | SAS YUEKI · SIREN 919 778 167 · adresse Aix-les-Bains · TVA FR54919778167 · contact anthony@methodr.io · fondation 13/09/2022 |
| `SoftwareApplication` | Catégorie BusinessApplication · sous-catégorie Sales Intelligence · OS iOS/Android/Web · 3 offres (Solo 49€, Équipe 79€, Entreprise 199€) · audience BusinessAudience |
| `WebSite` | URL, nom, langue fr-FR, publisher référencé |

### Sécurité & performance — vérifiés

- ✅ HTTPS actif avec HSTS (`Strict-Transport-Security: max-age=31536000`)
- ✅ Headers de sécurité : `X-Frame-Options: SAMEORIGIN`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin`
- ✅ Site mobile-friendly (responsive natif)
- ✅ Temps de chargement rapide (site statique servi par CDN Netlify)
- ✅ Accès totalement public (pas de mot de passe, pas de SSO)

**Conclusion de l'audit :** le site est au niveau d'un site B2B pro bien configuré. Google, Bing, LinkedIn, Facebook/WhatsApp, Slack, Twitter/X peuvent tous comprendre et afficher correctement le contenu.

---

## ⏳ PHASE 1 — Déclaration aux moteurs (à faire par Manu, ~15 min au total)

### Google Search Console — PRIORITÉ

- [ ] Créer un compte sur https://search.google.com/search-console
- [ ] Ajouter la propriété : choisir "Préfixe d'URL" → entrer `https://methodr.io`
- [ ] Méthode de vérification recommandée : **"Balise HTML"**
- [ ] Google fournit un code du type `<meta name="google-site-verification" content="abc123xyz..." />`
- [ ] Transmettre ce token à Claude pour ajout dans le `<head>` du site
- [ ] Une fois vérifié, **soumettre le sitemap** : aller dans "Sitemaps" → entrer `sitemap.xml` → Envoyer
- [ ] **Optionnel mais accélérateur** : utiliser "Inspection d'URL" sur `https://methodr.io/`, puis cliquer "Demander une indexation"

### Bing Webmaster Tools — complémentaire (5 min)

- [ ] Créer un compte sur https://www.bing.com/webmasters
- [ ] Choisir "Importer depuis Google Search Console" (1 clic, récupère tout automatiquement)
- [ ] Vérifier que le sitemap est bien pris en compte

### Google Business Profile — si pertinent

- [ ] Utile si tu souhaites apparaître sur Google Maps et dans les recherches locales "formation immobilier Aix-les-Bains"
- [ ] Créer la fiche SAS YUEKI sur https://www.google.com/business
- [ ] Catégorie : "Éditeur de logiciels" ou "Organisme de formation"
- [ ] Adresse : 725 boulevard Robert Barrier, 73100 Aix-les-Bains
- [ ] Vérification par courrier postal (délai ~10 jours)

---

## ⏳ PHASE 2 — Stratégie contenu (quand le produit est stabilisé)

### Architecture de pages
- [ ] Évaluer le passage du mono-page à un multi-page (une page par persona ou fonction = une porte d'entrée SEO)
- [ ] Toute modification d'URL → ajouter une redirection 301 dans `netlify.toml`
- [ ] Envisager une section `/blog/` ou `/ressources/` pour le contenu éditorial

### Articles SEO à fort potentiel (mots-clés métier)
Idées d'articles calibrés sur des intentions de recherche réelles :
- [ ] "Comment prendre un mandat exclusif — méthode R0/R1/R2"
- [ ] "Le plan de vente optimal de la prise de mandat vendeur"
- [ ] "R1 découverte vendeur : les 5 phases à ne pas rater"
- [ ] "R2 mandat exclusif : l'ancrage prix qui fait la différence"
- [ ] "Objection 'pas de vitrine' : comment la traiter en rendez-vous vendeur"
- [ ] "Dashboard commercial immobilier : piloter un réseau sans accompagnement physique"
- [ ] "Methodr vs CRM immobilier classique : quelle différence ?"

### Mots-clés cibles (à valider avec Google Keyword Planner)
- "prise de mandat exclusif immobilier"
- "méthode prise de mandat"
- "coaching mandataire immobilier"
- "formation R1 R2 immobilier"
- "scoring entretien vendeur"
- "DVF prise de mandat"
- "outil mandataire IAD Safti"

### Netlinking (backlinks)
- [ ] Annuaires pros immobilier (FNAIM, UNIS, Proprietaire.fr)
- [ ] Articles invités sur blogs immobilier (Immobilier 2.0, Le Mag de l'Immo, Solutions Agence)
- [ ] Product Hunt au lancement public
- [ ] Échanges de liens avec réseaux partenaires (IAD, Safti, 3% Immo)

### Tracking & analytics
- [ ] Ajouter un outil d'analytics respectueux RGPD :
  - **Option A** : Plausible (~9€/mois, hébergé UE, pas de bandeau cookie nécessaire)
  - **Option B** : Matomo self-hosted (gratuit mais à auto-héberger)
  - **Option C** : Google Analytics 4 (gratuit, nécessite bandeau cookies)
- [ ] Configurer les événements de conversion (inscription bêta, demande devis formation)
- [ ] Dashboard mensuel de suivi

---

## 📋 RÈGLES D'OR — à relire AVANT toute évolution du site

### Ce qui NE doit PAS changer sans précaution

1. **Les URLs indexées** — si une URL change, ajouter une redirection 301 dans `netlify.toml` :
   ```toml
   [[redirects]]
     from = "/ancienne-url"
     to = "/nouvelle-url"
     status = 301
   ```
2. **Le domaine principal** — rester sur `methodr.io` (ne migrer qu'en cas de nécessité absolue)
3. **Les fichiers `/robots.txt` et `/sitemap.xml`** — ne jamais supprimer, maintenir à jour

### Ce qui peut évoluer librement

- Le design, la palette, les typographies
- Les textes, titres, accroches (Google ré-indexe sous 7-14 jours)
- L'image OG
- Les sections internes de la page
- Les positionnements marketing

### En cas de pivot produit

1. Mettre à jour les `<title>` et `<meta description>` avec le nouveau positionnement
2. Actualiser le JSON-LD `SoftwareApplication` (catégorie, description, offres)
3. Régénérer l'image OG si le visuel change
4. Actualiser le contenu textuel du site
5. Dans Google Search Console : faire une "Demande d'indexation" pour accélérer la re-prise en compte
6. **Mettre à jour ce fichier `SEO-ROADMAP.md`**

---

## 🔧 Checklist technique à surveiller

À vérifier régulièrement (mensuel dès qu'il y a du trafic) :

- [ ] Toutes les pages indexées renvoient HTTP 200 (pas de 404)
- [ ] Certificat SSL valide et non expiré
- [ ] Performances de chargement stables (PageSpeed Insights)
- [ ] Aucune erreur dans Google Search Console
- [ ] Sitemap à jour (contient toutes les pages publiques)
- [ ] JSON-LD valide (test sur https://search.google.com/test/rich-results)
- [ ] Image OG toujours accessible (test sur LinkedIn Post Inspector)

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
| Google Keyword Planner | ads.google.com (tools) | Volumes de recherche (compte Google Ads requis) |

---

## 📊 Indicateurs à suivre une fois le trafic démarré

| KPI | Cible 3 mois | Cible 6 mois | Cible 12 mois |
|---|---|---|---|
| Pages indexées sur Google | 4+ | 10+ | 30+ |
| Impressions Search Console / mois | 100+ | 500+ | 2000+ |
| Clics organiques / mois | 10+ | 50+ | 200+ |
| Position moyenne "methodr" | Top 3 | Top 1 | Top 1 |
| Position "prise de mandat exclusif" | Hors top 100 | Top 50 | Top 20 |
| Backlinks externes | 1-2 | 5-10 | 20+ |

---

## 📝 Journal des modifications SEO

| Date | Action | Auteur | Résultat |
|---|---|---|---|
| 17/04/2026 | Déploiement initial robots.txt + sitemap.xml + JSON-LD + meta OG | Claude | Fondations techniques OK |
| 17/04/2026 | Mise à jour image OG vers charte v3 (blanc + indigo + Inter) | Claude | Cohérence visuelle des partages sociaux |
| 19/04/2026 | Audit SEO complet du site en production | Claude | Tout le minimum vital confirmé en place |
| 19/04/2026 | Création du fichier SEO-ROADMAP.md (cette version) | Claude | Fichier de suivi permanent en place |
| 19/04/2026 | Ajout balise google-site-verification dans le `<head>` + fichier HTML de vérification à la racine | Claude | 2 méthodes de vérification Google Search Console actives en production |
| 19/04/2026 | Validation de la propriété dans Google Search Console | Manu | ✅ Propriété validée · accueil indexé · HTTPS confirmé · demande d'indexation effectuée |
| _à compléter_ | Soumission sitemap.xml dans Google Search Console | Manu | _à documenter_ |
| _à compléter_ | Vérifier indexation des 3 pages légales (sous 72h) | Manu | _à documenter_ |

---

## ℹ️ Contact technique pour la suite

- **Repo GitHub** : https://github.com/manu23232323/Methodr-Landing
- **Netlify** : https://app.netlify.com/projects/methodr-landing
- **Domaine** : methodr.io (DNS hébergé chez Infomaniak, A record `75.2.60.5`, AAAA + CNAME www configurés)
- **Protocole de déploiement** : consulter `PROTOCOLE-SITES.md` dans le projet
