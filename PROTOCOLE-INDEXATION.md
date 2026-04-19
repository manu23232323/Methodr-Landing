# PROTOCOLE INDEXATION & SEO — MANU POZZANI
## Fichier référentiel — À suivre étape par étape pour référencer n'importe quel site

> **Principe** : ce protocole a été **testé et validé** sur `methodr.io` le 19/04/2026. Il est **réplicable à l'identique** pour chaque nouveau site lancé. Compter 30 minutes de travail total (technique + console), puis 24-72h d'attente pour l'indexation.

---

## 🎯 OBJECTIF ET THÉORIE

### Ce que signifie "être référencé sur Google"

Un site web existe sur Internet dès qu'il a un nom de domaine et un hébergement. **Mais il n'existe pour Google que lorsque Google le sait.** Le référencement, c'est l'ensemble des actions qui font passer le site de l'état *inconnu* à l'état *indexé* dans les moteurs de recherche.

### Les 3 niveaux de référencement

| Niveau | Objectif | Temps |
|---|---|---|
| **1. Technique (indispensable)** | Google peut trouver, lire et comprendre le site | 30 min — une fois |
| **2. Déclaration (indispensable)** | Google sait que le site existe et l'a ajouté à son index | 24-72h |
| **3. Contenu (long terme)** | Le site ressort pour des mots-clés métier | 6-18 mois |

**Ce protocole couvre les niveaux 1 et 2.** Le niveau 3 relève d'une stratégie éditoriale propre à chaque projet.

### Ce que Google regarde quand il découvre un site

1. **`robots.txt`** — permission de crawler
2. **`sitemap.xml`** — liste des pages à découvrir
3. **Balises meta** (`<title>`, `<meta description>`, Open Graph, canonical) — nature du contenu
4. **Données structurées JSON-LD** (schema.org) — nature de l'entité (entreprise, produit, service)
5. **HTTPS + performance** — signaux de qualité
6. **Mobile-friendly** — compatibilité responsive

Si tous ces éléments sont en place avant la déclaration, l'indexation est quasi immédiate.

---

## 📋 PRÉ-REQUIS AVANT DE LANCER L'INDEXATION

À vérifier dans l'ordre. Si un point manque, **ne pas déclarer le site à Google**, régler d'abord.

### Pré-requis techniques site

- [ ] Le site est **en production** sur son domaine final (pas uniquement sur l'URL Netlify)
- [ ] **HTTPS actif** avec certificat SSL valide
- [ ] Toutes les pages principales répondent en **HTTP 200**
- [ ] Le site est **responsive** (mobile-friendly)
- [ ] Les **pages légales sont publiées** (mentions légales, politique de confidentialité, CGU/CGV si nécessaire)

### Pré-requis contenu

- [ ] Un seul `<title>` **unique et descriptif** par page (60-70 caractères max)
- [ ] Une `<meta description>` **unique et accrocheuse** par page (150-160 caractères max)
- [ ] Un `<html lang="fr">` (ou autre langue) sur chaque page
- [ ] Une **balise canonical** `<link rel="canonical" href="https://DOMAINE/PAGE">` sur chaque page
- [ ] Une **image Open Graph** 1200×630 px accessible à une URL publique

---

## ⚙️ PHASE 1 — MINIMUM VITAL TECHNIQUE (30 min)

### Étape 1.1 — Créer `robots.txt` à la racine

**Fichier à déposer** : `robots.txt` à la racine du site.

```
# robots.txt pour DOMAINE
# Autorise tous les moteurs de recherche à indexer tout le site

User-agent: *
Allow: /

# Emplacement du sitemap
Sitemap: https://DOMAINE/sitemap.xml
```

**Vérification** : `https://DOMAINE/robots.txt` doit retourner HTTP 200 avec ce contenu.

### Étape 1.2 — Créer `sitemap.xml` à la racine

**Fichier à déposer** : `sitemap.xml` à la racine du site. Inclure toutes les pages publiques.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://DOMAINE/</loc>
    <lastmod>YYYY-MM-DD</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://DOMAINE/mentions-legales</loc>
    <lastmod>YYYY-MM-DD</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.3</priority>
  </url>
  <!-- Ajouter toutes les autres pages publiques -->
</urlset>
```

**Règles de priorité** :
- Accueil : `1.0`
- Pages produit/tarifs/contact : `0.8`
- Articles de blog : `0.7`
- Pages légales : `0.3`

**Vérification** : `https://DOMAINE/sitemap.xml` doit retourner HTTP 200 avec le XML.

### Étape 1.3 — Enrichir le `<head>` de chaque page

**Bloc minimal à placer dans chaque page** (adapter le contenu à la page) :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Balises de base (uniques par page) -->
<title>TITRE DE LA PAGE — NOM DU SITE</title>
<meta name="description" content="Description accrocheuse de 150-160 caractères.">
<meta name="author" content="NOM ÉDITEUR LÉGAL">
<meta name="robots" content="index, follow, max-image-preview:large">
<meta name="language" content="French">
<link rel="canonical" href="https://DOMAINE/URL-DE-LA-PAGE">

<!-- Open Graph (partages Facebook, LinkedIn, WhatsApp, Slack) -->
<meta property="og:title" content="TITRE">
<meta property="og:description" content="DESCRIPTION">
<meta property="og:url" content="https://DOMAINE/URL-DE-LA-PAGE">
<meta property="og:image" content="https://DOMAINE/assets/og-image.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:site_name" content="NOM DU SITE">
<meta property="og:locale" content="fr_FR">
<meta property="og:type" content="website">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="TITRE">
<meta name="twitter:description" content="DESCRIPTION">
<meta name="twitter:image" content="https://DOMAINE/assets/og-image.png">
</head>
```

### Étape 1.4 — Ajouter les données structurées JSON-LD

**Pourquoi** : permet à Google de comprendre la nature du site (entreprise, produit, service, prix…) et d'afficher des résultats enrichis.

**Bloc à placer dans le `<head>` de la page d'accueil** (adapter à chaque projet) :

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://DOMAINE/#organization",
      "name": "NOM COMMERCIAL",
      "legalName": "RAISON SOCIALE",
      "url": "https://DOMAINE",
      "logo": "https://DOMAINE/assets/og-image.png",
      "description": "Description de l'activité.",
      "foundingDate": "YYYY-MM-DD",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "ADRESSE",
        "postalCode": "CP",
        "addressLocality": "VILLE",
        "addressCountry": "FR"
      },
      "vatID": "FR00000000000",
      "taxID": "SIREN",
      "email": "contact@DOMAINE"
    },
    {
      "@type": "SoftwareApplication",
      "@id": "https://DOMAINE/#software",
      "name": "NOM PRODUIT",
      "applicationCategory": "BusinessApplication",
      "applicationSubCategory": "PRÉCISER",
      "operatingSystem": "iOS, Android, Web",
      "url": "https://DOMAINE",
      "description": "Description du produit.",
      "publisher": {"@id": "https://DOMAINE/#organization"},
      "offers": [
        {
          "@type": "Offer",
          "name": "NOM OFFRE",
          "price": "XX",
          "priceCurrency": "EUR",
          "priceSpecification": {
            "@type": "UnitPriceSpecification",
            "price": "XX",
            "priceCurrency": "EUR",
            "billingIncrement": 1,
            "unitText": "MON"
          }
        }
      ]
    },
    {
      "@type": "WebSite",
      "@id": "https://DOMAINE/#website",
      "url": "https://DOMAINE",
      "name": "NOM DU SITE",
      "inLanguage": "fr-FR",
      "publisher": {"@id": "https://DOMAINE/#organization"}
    }
  ]
}
</script>
```

**Choisir le bon `@type`** selon le projet :
- **SaaS / app mobile** : `SoftwareApplication`
- **Site vitrine / prestataire de services** : `ProfessionalService` ou `LocalBusiness`
- **E-commerce** : `Store` ou `OnlineStore`
- **Média / blog** : `NewsMediaOrganization` ou simplement `Organization`
- **Organisme de formation** : `EducationalOrganization`

**Validation** : une fois déployé, tester le JSON-LD sur https://search.google.com/test/rich-results

### Étape 1.5 — Créer et déployer l'image OG

**Spécifications** :
- Format : **1200 × 630 px** exactement (standard OG)
- Poids : **< 200 KB** idéalement
- Contenu : logo + titre court + visuel ou sous-titre
- Format : **PNG** (ou JPG)
- URL finale : `https://DOMAINE/assets/og-image.png` (ou autre chemin stable)

**À déployer dans** : le repo GitHub, typiquement dans un dossier `/assets/`.

---

## ⚙️ PHASE 2 — DÉCLARATION AUX MOTEURS (15 min — action humaine nécessaire)

### Étape 2.1 — Google Search Console

**Compte Google à utiliser** : celui de l'éditeur légal (pas un compte personnel si le projet est destiné à être revendu).

**Protocole en 7 clics** :

1. Aller sur https://search.google.com/search-console
2. Cliquer **"Ajouter une propriété"** → choisir **"Préfixe d'URL"**
3. Entrer `https://DOMAINE` (avec HTTPS, sans slash final)
4. Choisir la méthode **"Balise HTML"** (la plus simple)
5. Google fournit un code du type :
   ```html
   <meta name="google-site-verification" content="TOKEN_UNIQUE_A_REPORTER" />
   ```
6. **Action technique** : ajouter cette balise dans le `<head>` de l'index, juste après `<meta viewport>`. Push, attendre le rebuild (~30s).
7. **Méthode de secours recommandée** (optionnel mais sécurisant) : Google propose aussi un fichier HTML à la racine (`googleXXXXXX.html`). Déployer les **deux méthodes en parallèle** maximise les chances de succès.
8. Retourner dans Google Search Console et cliquer **"Vérifier"**.

**Validation** : Google affiche ✅ "La propriété a bien été validée."

### Étape 2.2 — Soumettre le sitemap

1. Dans Google Search Console, menu gauche → **"Sitemaps"**
2. Dans "Ajouter un sitemap", entrer simplement : `sitemap.xml`
3. Cliquer **"Envoyer"**
4. Résultat attendu : **"Opération effectuée"** avec le nombre d'URLs découvertes correspondant au sitemap

### Étape 2.3 — Forcer l'indexation de l'accueil (optionnel mais recommandé)

1. En haut de l'interface, barre **"Inspection d'URL"** → coller `https://DOMAINE/`
2. Google va analyser l'URL
3. Cliquer **"Demander l'indexation"**
4. Google met la page en file prioritaire → indexation en **24-72h** au lieu de 2-4 semaines

### Étape 2.4 — Bing Webmaster Tools (optionnel, 5 min)

**Bing = 3-5% des recherches FR**, mais c'est aussi le moteur derrière DuckDuckGo, Ecosia, Yahoo, et Copilot (ChatGPT aussi utilise Bing). Donc intéressant à couvrir.

1. Aller sur https://www.bing.com/webmasters
2. Se connecter avec un compte Microsoft (ou en créer un)
3. Cliquer **"Ajouter un site"** → choisir **"Importer depuis Google Search Console"**
4. Bing récupère automatiquement la propriété + le sitemap

### Étape 2.5 — Google Business Profile (si pertinent)

**À faire uniquement si** :
- Le projet a une adresse physique visible
- Les clients peuvent te rechercher localement ("X à VILLE")

Si oui : https://www.google.com/business → créer la fiche.

---

## 📊 PHASE 3 — SUIVI ET VALIDATION

### Jour J (soumission)

- Accueil normalement indexé dans les **quelques minutes** suivant le clic "Demander l'indexation"
- Vérifier Google Search Console → "Inspection d'URL" → **"Cette URL est sur Google"**

### J+3 à J+7

- Les autres pages du sitemap passent au statut indexé
- Vérifier dans Google Search Console → "Pages" → voir le nombre d'URLs indexées
- Dans Google en navigation privée, taper `site:DOMAINE` → toutes les pages doivent apparaître

### J+14

- Premières "impressions" dans Google Search Console → "Performances"
- Cliquer sur "Requêtes" pour voir sur quels mots-clés le site apparaît
- Typiquement : le nom de marque et quelques mots-clés naturels (pas encore de volume)

### J+30 et au-delà

- Suivi mensuel des impressions / clics / position moyenne
- Mise à jour du fichier **`SEO-ROADMAP.md`** du site (journal des modifications)
- Début de la Phase 3 (contenu éditorial) si stratégie SEO active

---

## 🔄 SI PIVOT OU REFONTE DU SITE

### Ce qui survit sans effort

- `robots.txt`, `sitemap.xml`, Google Search Console, JSON-LD génériques, HTTPS — tout reste valide

### Ce qui peut évoluer librement

- Design, typographie, palette, image OG
- Textes, titres, accroches (Google ré-indexe sous 7-14 jours)
- Positionnement marketing

### Ce qui demande une précaution

- **Changement d'URL** : ajouter une redirection 301 dans `netlify.toml` :
  ```toml
  [[redirects]]
    from = "/ancienne-url"
    to = "/nouvelle-url"
    status = 301
  ```
- **Changement de domaine** : reconfigurer Google Search Console (nouvelle propriété) + 301 depuis l'ancien domaine
- **Suppression de pages** : les retirer du sitemap, et idéalement rediriger vers une page proche

### Après tout changement majeur

Dans Google Search Console : "Inspection d'URL" → "Demander l'indexation" pour accélérer la re-prise en compte.

---

## 📝 HISTORIQUE DES INDEXATIONS

| Site | Date Phase 1 | Date Phase 2 | Fichier suivi dédié |
|---|---|---|---|
| **methodr.io** | 17/04/2026 | 19/04/2026 | `SEO-ROADMAP.md` dans le projet Methodr |
| _future indexation_ | _à documenter_ | _à documenter_ | _à créer_ |

---

## 📚 OUTILS DE RÉFÉRENCE (tous gratuits)

| Outil | URL | Usage |
|---|---|---|
| Google Search Console | search.google.com/search-console | Monitoring indexation + trafic organique |
| Bing Webmaster | bing.com/webmasters | Idem pour Bing |
| PageSpeed Insights | pagespeed.web.dev | Tester les perfs |
| Rich Results Test | search.google.com/test/rich-results | Valider le JSON-LD |
| Mobile-Friendly Test | search.google.com/test/mobile-friendly | Vérifier responsive |
| LinkedIn Post Inspector | linkedin.com/post-inspector | Rafraîchir cache OG LinkedIn |
| Facebook Sharing Debugger | developers.facebook.com/tools/debug | Rafraîchir cache OG Facebook/WhatsApp |
| Google Keyword Planner | ads.google.com (tools) | Volumes de recherche |

---

## ✅ CHECKLIST COMPLÈTE À SUIVRE POUR CHAQUE NOUVEAU SITE

### Phase 1 — Technique (automatique via Claude + MCP Netlify)
- [ ] `robots.txt` à la racine
- [ ] `sitemap.xml` à la racine avec toutes les URLs
- [ ] `<title>` unique par page
- [ ] `<meta description>` unique par page
- [ ] `<link rel="canonical">` sur chaque page
- [ ] `<meta robots>` en index/follow
- [ ] Open Graph complet (10 balises)
- [ ] Twitter Card
- [ ] JSON-LD schema.org (Organization + entité principale + WebSite)
- [ ] Image OG 1200×630 déployée
- [ ] HTTPS + HSTS actifs
- [ ] Site mobile-friendly

### Phase 2 — Déclaration (action humaine)
- [ ] Compte Google Search Console créé
- [ ] Propriété `https://DOMAINE` ajoutée
- [ ] Token de vérification récupéré
- [ ] Balise meta ajoutée au `<head>` (Claude)
- [ ] Fichier HTML de vérification ajouté à la racine (Claude, méthode de secours)
- [ ] Clic "Vérifier" réussi
- [ ] Sitemap soumis et "Opération effectuée"
- [ ] Inspection d'URL + Demande d'indexation pour l'accueil
- [ ] Bing Webmaster Tools (optionnel)
- [ ] Google Business Profile (si pertinent)

### Phase 3 — Fichier de suivi du site
- [ ] Créer `SEO-ROADMAP.md` dédié au site dans le repo
- [ ] Documenter les actions réalisées avec dates
- [ ] Planifier les révisions mensuelles

---

*Dernière mise à jour : 19 avril 2026 — Protocole validé sur methodr.io*
