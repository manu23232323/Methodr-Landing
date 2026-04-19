# PROTOCOLE SITES INTERNET — MANU POZZANI
## Fichier référentiel — À consulter systématiquement avant toute création ou modification de site

> **Deux fichiers protocoles complémentaires :**
> - **`PROTOCOLE-SITES.md`** (ce fichier) : création, déploiement, DNS, formulaires, pages légales
> - **`PROTOCOLE-INDEXATION.md`** : référencement Google Search Console + Bing + SEO minimum vital

---

## CREDENTIALS & ACCÈS

| Service | Compte | Token / Accès |
|---|---|---|
| **GitHub** | `manu23232323` | Token personnel `ghp_***` sans expiration — **stocké dans les variables d'env Manu, ne jamais committer en clair** |
| **Netlify** | `manu23232323's team` | MCP Netlify authentifié dans Claude.ai — permanent |
| **Team ID Netlify** | `6932bdb2b0a203fdb0d09066` | Permanent |
| **Team Slug Netlify** | `manu23232323` | Permanent |
| **DNS** | Infomaniak — accès manuel uniquement | Pas de MCP disponible |

> ✅ Le token GitHub est sans expiration. Le MCP Netlify est authentifié en permanence. Le token GitHub n'est jamais écrit en clair dans les fichiers du repo — il est fourni à Claude au début de chaque session via le context projet ou via la mémoire de Claude.

---

## INVENTAIRE DES SITES

### 1. methodr-landing
| Champ | Valeur |
|---|---|
| **Projet** | Methodr — plateforme d'intelligence commerciale terrain pour l'immobilier |
| **Netlify Site ID** | `30bdb973-485a-4395-ad7e-432a53df0cb5` |
| **Netlify URL** | https://app.netlify.com/projects/methodr-landing |
| **URL live** | https://methodr.io |
| **URL Netlify** | https://methodr-landing.netlify.app |
| **GitHub repo** | `manu23232323/Methodr-Landing` (branche `main`) |
| **Formulaires Netlify** | `beta-methodr` (ID `69d63122d2465f0008d63240`) + `contact-formation` (ID `69e1fbe16819280009af2009`) — notifications email vers `manu@methodr.io` configurées |
| **Pages publiées** | `/` (accueil) + `/mentions-legales` + `/confidentialite` + `/cgu` (via `netlify.toml`) |
| **Domaines DNS** | `methodr.io` (A + AAAA) + `www.methodr.io` (CNAME) |
| **DNS hébergé** | Infomaniak |
| **Technologie** | HTML statique — `index.html` + pages légales + `legal.css` + `netlify.toml` |
| **Design actuel** | v3 — Inter + accent indigo `#4f46e5` + curseur météorite indigo |
| **SEO** | ✅ Indexation Google Search Console validée 19/04/2026 · sitemap soumis (4 URLs) · voir `SEO-ROADMAP.md` du repo |
| **Dernière modif** | 19 avril 2026 |

---

### 2. spagybio
| Champ | Valeur |
|---|---|
| **Projet** | Spagybio — e-commerce élixirs spagyriques |
| **Netlify Site ID** | `3c23e7d4-0abe-46ea-9c72-3ed18966faa9` |
| **Netlify URL** | https://app.netlify.com/projects/spagybio |
| **URL live** | https://spagybio.netlify.app |
| **GitHub repo** | À confirmer |
| **Formulaires** | Activés |
| **Technologie** | HTML statique |
| **SEO** | Non indexé à ce jour |

---

### 3. l-ancre.fr (prismatic-alfajores-62b748)
| Champ | Valeur |
|---|---|
| **Projet** | L'Ancre |
| **Netlify Site ID** | `3bc545d3-f0e5-48aa-9c58-d0fdb7552a5f` |
| **Netlify URL** | https://app.netlify.com/projects/prismatic-alfajores-62b748 |
| **URL live** | https://l-ancre.fr |
| **GitHub repo** | À confirmer |
| **Formulaires** | Activés |
| **Technologie** | HTML statique |
| **SEO** | Non indexé à ce jour |

---

### 4. k23.fr (k23-site)
| Champ | Valeur |
|---|---|
| **Projet** | K23 |
| **Netlify Site ID** | `7ee1d1ae-8ed6-4d7b-8ebf-51afd25b3d60` |
| **Netlify URL** | https://app.netlify.com/projects/k23-site |
| **URL live** | https://k23.fr |
| **GitHub repo** | À confirmer |
| **Formulaires** | Non activés |
| **Technologie** | HTML statique |
| **SEO** | Non indexé à ce jour |

---

### 5. formalita.fr (formalita-landing)
| Champ | Valeur |
|---|---|
| **Projet** | Formalita |
| **Netlify Site ID** | `2223fae8-6e90-4fe9-932e-9e7d2ac77e1b` |
| **Netlify URL** | https://app.netlify.com/projects/formalita-landing |
| **URL live** | https://formalita.fr |
| **GitHub repo** | À confirmer |
| **Formulaires** | Activés |
| **Technologie** | HTML statique |
| **SEO** | Non indexé à ce jour |

---

### 6. yueki-formation
| Champ | Valeur |
|---|---|
| **Projet** | YUEKI Formation — organisme de formation certifié Qualiopi |
| **Netlify Site ID** | `1f98151c-ab5a-477f-b258-a53d4e78eabc` |
| **Netlify URL** | https://app.netlify.com/projects/yueki-formation |
| **URL live** | https://yueki-formation.netlify.app |
| **GitHub repo** | `manu23232323/yueki-formation` (branche `main`) |
| **Formulaires** | Activés |
| **GitHub connecté à Netlify** | ✅ Oui — déploiement automatique au push |
| **Technologie** | HTML statique — fichier unique `index.html` |
| **DNS cutover à faire** | yueki-formation.fr hébergé chez o2switch — pointer vers Netlify quand accès cPanel obtenu |
| **SEO** | Non indexé à ce jour |
| **Dernière modif** | 14 avril 2026 |

---

## PROTOCOLE — CRÉATION D'UN NOUVEAU SITE

### Étapes dans l'ordre

**1. Créer le repo GitHub**
```bash
curl -s -X POST \
  -H "Authorization: token $GH_TOKEN" \
  https://api.github.com/user/repos \
  -d '{"name":"NOM-DU-REPO","private":true}'
```

**2. Créer le site sur Netlify**
- Team slug : `manu23232323`
- Team ID : `6932bdb2b0a203fdb0d09066`
- Nom : format `kebab-case` (ex: `methodr-landing`)

**3. Pousser le fichier index.html sur GitHub**
```bash
CONTENT=$(base64 -w 0 /chemin/vers/index.html)
curl -s -X PUT \
  -H "Authorization: token $GH_TOKEN" \
  https://api.github.com/repos/manu23232323/NOM-REPO/contents/index.html \
  -d "{\"message\":\"Initial commit\",\"content\":\"$CONTENT\"}"
```

> ⚠️ Si le fichier est volumineux (> 50 KB), utiliser Python :
```python
import base64, json, urllib.request
with open('index.html', 'rb') as f:
    content = base64.b64encode(f.read()).decode()
payload = json.dumps({"message": "Initial commit", "content": content}).encode()
req = urllib.request.Request(
    "https://api.github.com/repos/manu23232323/NOM-REPO/contents/index.html",
    data=payload, method="PUT",
    headers={"Authorization": f"token {GH_TOKEN}", "Content-Type": "application/json", "User-Agent": "Claude"}
)
urllib.request.urlopen(req)
```

**4. Premier déploiement Netlify (avant connexion GitHub)**

Le MCP Netlify génère un proxy token via `deploy-site`. Utiliser ce token pour POSTer le ZIP :
```python
import urllib.request, zipfile, io, uuid

SITE_ID = "SITE_ID_ICI"
proxy_token = "TOKEN_GÉNÉRÉ_PAR_MCP"
upload_url = f"https://netlify-mcp.netlify.app/proxy/{proxy_token}/api/v1/sites/{SITE_ID}/builds"

boundary = f"----NetlifyFormBoundary{uuid.uuid4().hex}"
zip_buffer = io.BytesIO()
with zipfile.ZipFile(zip_buffer, 'w', zipfile.ZIP_DEFLATED) as zf:
    with open('index.html', 'rb') as f:
        zf.writestr('index.html', f.read())
zip_data = zip_buffer.getvalue()

parts = [
    f"--{boundary}\r\nContent-Disposition: form-data; name=\"zip\"; filename=\"deploy.zip\"\r\nContent-Type: application/zip\r\n\r\n".encode(),
    zip_data,
    f"\r\n--{boundary}--\r\n".encode()
]
body = b"".join(parts)

req = urllib.request.Request(upload_url, data=body, method="POST", headers={
    "Content-Type": f"multipart/form-data; boundary={boundary}",
    "Content-Length": str(len(body)),
    "User-Agent": "netlify-mcp"
})
urllib.request.urlopen(req)
```

**5. Autoriser Netlify sur GitHub** (manuel — une seule fois par repo)
→ https://github.com/apps/netlify/installations/new

**6. Connecter GitHub → Netlify** (manuel depuis l'interface)
→ https://app.netlify.com/projects/NOM-SITE/link-repos
→ Sélectionner le repo, branche `main`, tous les autres champs vides

**7. Activer les formulaires Netlify**
- Ajouter `data-netlify="true"` + `name="form-name"` + champ `name` sur chaque input
- Activer via MCP : `update-forms → enabled`

**8. Configurer le domaine custom** (si applicable)
```bash
curl -s -X PATCH \
  "https://api.netlify.com/api/v1/sites/$SITE_ID" \
  -H "Authorization: Bearer $NF_TOKEN" \
  -d '{"custom_domain":"domaine.io","domain_aliases":["www.domaine.io"]}'
```

**9. Ajouter les DNS chez Infomaniak** (manuel)
- A record : `@` → `75.2.60.5`
- AAAA record : `@` → `2a05:d018:76c:b685:b29e:1a5a:3e49:8b34`
- CNAME : `www` → `NOM-SITE.netlify.app`

**10. Publier les pages légales** (voir protocole dédié ci-dessous)

**11. Lancer le minimum vital SEO** (voir `PROTOCOLE-INDEXATION.md`)

---

## PROTOCOLE — MODIFICATION D'UN SITE EXISTANT

### Étapes dans l'ordre

**1. Récupérer le SHA actuel du fichier**
```python
import urllib.request, json
req = urllib.request.Request(
    "https://api.github.com/repos/manu23232323/NOM-REPO/contents/index.html",
    headers={"Authorization": f"token {GH_TOKEN}", "User-Agent": "Claude"}
)
r = json.loads(urllib.request.urlopen(req).read())
sha = r['sha']
```

**2. Encoder et pousser le fichier modifié**
```python
import base64, json, urllib.request
with open('index.html', 'rb') as f:
    content = base64.b64encode(f.read()).decode()
payload = json.dumps({"message": "Mise à jour", "content": content, "sha": sha}).encode()
req = urllib.request.Request(
    "https://api.github.com/repos/manu23232323/NOM-REPO/contents/index.html",
    data=payload, method="PUT",
    headers={"Authorization": f"token {GH_TOKEN}", "Content-Type": "application/json", "User-Agent": "Claude"}
)
urllib.request.urlopen(req)
```

**3. Netlify redéploie automatiquement** — délai ~30 secondes

**4. Vérifier le déploiement**
```bash
curl -s \
  "https://api.netlify.com/api/v1/sites/$SITE_ID/deploys?per_page=1" \
  -H "Authorization: Bearer $NF_TOKEN" | python3 -c "
import sys,json; r=json.load(sys.stdin)
if r: print('State:', r[0].get('state','?'))"
```

**5. Si refonte majeure ou changement d'URL** :
- Ajouter les redirections 301 dans `netlify.toml` (voir règles plus bas)
- Régénérer l'image OG si visuel changé
- Dans Google Search Console → Inspection d'URL → Demander l'indexation pour accélérer la re-prise en compte

---

## PROTOCOLE — PAGES LÉGALES (obligatoires RGPD / LCEN)

### Pages minimales à publier pour tout site commercial français

1. **Mentions légales** (`/mentions-legales`) — LCEN : éditeur, hébergeur, directeur de publication, contact
2. **Politique de confidentialité** (`/confidentialite`) — RGPD : données collectées, sous-traitants, droits utilisateur
3. **CGU ou CGV** (`/cgu` ou `/cgv`) — conditions d'utilisation ou de vente selon le modèle

### Protocole de mise en URL propre via netlify.toml

Créer un fichier `netlify.toml` à la racine du repo :

```toml
# Redirections vers URLs propres (sans .html)
[[redirects]]
  from = "/mentions-legales"
  to = "/mentions-legales.html"
  status = 200

[[redirects]]
  from = "/confidentialite"
  to = "/confidentialite.html"
  status = 200

[[redirects]]
  from = "/cgu"
  to = "/cgu.html"
  status = 200

# Headers de sécurité (bonus SEO)
[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "SAMEORIGIN"
    X-Content-Type-Options = "nosniff"
    Referrer-Policy = "strict-origin-when-cross-origin"
```

### Template minimal des pages légales

Pour chaque page légale :
- Doctype HTML5 + `<html lang="fr">`
- Balises `<title>` et `<meta description>` adaptées
- CSS commun dans un fichier séparé (`/legal.css`)
- Lien retour vers l'accueil en haut de page
- Footer avec liens croisés entre les 3 pages légales

### Contenu minimum mentions légales

- Nom commercial + raison sociale (SAS / SARL / EI…)
- SIREN / SIRET
- Numéro TVA intracommunautaire
- Code NAF / APE
- Adresse du siège social
- Nom du directeur de la publication
- Hébergeur (Netlify : 2325 3rd Street, Suite 215, San Francisco, CA 94107, USA)
- Email de contact

### Contenu minimum politique de confidentialité (RGPD)

- Données collectées (formulaires, cookies techniques)
- Finalités du traitement
- Sous-traitants (Netlify, et tout autre prestataire audio/IA/email)
- Durée de conservation
- Droits utilisateur (accès, rectification, opposition, suppression, portabilité)
- Email de contact DPO

### Contenu minimum CGU

- Objet du contrat
- Description du service
- Obligations utilisateur
- Propriété intellectuelle
- Limitation de responsabilité
- Droit applicable + tribunal compétent
- Conditions de modification

---

## PROTOCOLE — LECTURE DES FORMULAIRES

```bash
curl -s \
  "https://api.netlify.com/api/v1/forms/$FORM_ID/submissions?per_page=20" \
  -H "Authorization: Bearer $NF_TOKEN" | python3 -c "
import sys, json
r = json.load(sys.stdin)
for s in r:
    d = s.get('data', {})
    fields = {k:v for k,v in d.items() if k not in ['ip','user_agent','referrer','bot-field']}
    print(s.get('created_at','?')[:10], '|', fields)"
```

---

## PROTOCOLE — SEO & INDEXATION

> **Pour le référencement d'un site sur Google et Bing, voir le fichier dédié `PROTOCOLE-INDEXATION.md`.**

### Résumé en 2 temps

**Phase 1 — Minimum vital technique** (Claude, ~30 min)
- `robots.txt` + `sitemap.xml` à la racine
- Balises meta (title, description, robots, canonical, lang) sur toutes les pages
- Open Graph + Twitter Card
- Données structurées JSON-LD (schema.org)
- Image OG 1200×630

**Phase 2 — Déclaration aux moteurs** (Manu, ~15 min)
- Créer la propriété dans Google Search Console
- Récupérer le token de vérification
- Claude ajoute la balise + fichier HTML de vérification
- Clic "Vérifier" côté Google
- Soumettre le sitemap
- Demander l'indexation manuelle de l'accueil
- (Optionnel) Importer dans Bing Webmaster Tools

**Phase 3 — Suivi** : créer un fichier `SEO-ROADMAP.md` dédié dans le repo pour documenter les actions et l'évolution.

---

## RÈGLES & CONTRAINTES IMPORTANTES

### DNS & Domaines
- `methodr.io` → site vitrine uniquement — **ne jamais utiliser pour cold email**
- `methodr.fr` + `methodr.app` → cold email uniquement (Instantly)
- DNS hébergé chez Infomaniak — accès manuel, pas de MCP

### Redirections 301 — règle d'or
Toute URL indexée qui change doit avoir une redirection 301 dans `netlify.toml` :
```toml
[[redirects]]
  from = "/ancienne-url"
  to = "/nouvelle-url"
  status = 301
```
Sans ça, le SEO accumulé sur l'ancienne URL est perdu.

### Formulaires Netlify
- Plan Free : 100 soumissions/mois — suffisant pour la bêta
- Notifications email automatiques : plan payant uniquement
- Solution alternative : lecture manuelle via API sur demande, OU configuration manuelle par Manu dans l'interface Netlify (Forms → notifications)
- **Checklist formulaire fonctionnel** :
  - `<form data-netlify="true" name="NOM" method="POST">`
  - `<input type="hidden" name="form-name" value="NOM">`
  - Chaque `<input>` et `<select>` doit avoir un attribut `name`
  - Ne pas intercepter avec `onsubmit` JS (empêche la capture)
  - Pour activer les formulaires, ajouter un formulaire hidden en haut du body qui liste tous les champs (détection au build)

### Sécurité tokens
- Ne jamais stocker les tokens en clair dans le code
- GitHub token : scope `repo` minimum
- Netlify token : généré sur https://app.netlify.com/user/applications/personal
- GitHub token : généré sur https://github.com/settings/tokens/new

### Netlify plan actuel
- Plan : **Free (Personal)**
- Team slug : `manu23232323`
- Team ID : `6932bdb2b0a203fdb0d09066`
- Limites : 100 soumissions formulaire/mois, pas de notifications email natives

### Déploiement — cas particuliers

**Si `npx` ou certains outils Netlify ne fonctionnent pas** (restrictions réseau container) :
1. Générer un proxy token via MCP `netlify-deploy-services-updater`
2. POST multipart/form-data ZIP vers `https://netlify-mcp.netlify.app/proxy/{token}/api/v1/sites/{siteId}/builds`
3. Utiliser Python `urllib` (pas curl, limites de taille d'argument pour les gros fichiers HTML 300KB+)
4. Boundary format : `----NetlifyFormBoundary{uuid}`
5. Set `Content-Length` explicitement

---

## RÉFÉRENCE IP NETLIFY

| Type | Valeur | Usage |
|---|---|---|
| A (IPv4) | `75.2.60.5` | Domaine racine `@` |
| AAAA (IPv6) | `2a05:d018:76c:b685:b29e:1a5a:3e49:8b34` | Domaine racine `@` |
| CNAME | `NOM-SITE.netlify.app` | Sous-domaine `www` |

---

## FICHIERS COMPLÉMENTAIRES DU PROJET

| Fichier | Contenu | Localisation |
|---|---|---|
| `PROTOCOLE-SITES.md` | Ce fichier — création/modif/déploiement | Projet Claude + repo principal |
| `PROTOCOLE-INDEXATION.md` | Référencement SEO Google/Bing | Projet Claude + repo principal |
| `SEO-ROADMAP.md` | Suivi SEO spécifique par site (créé par site) | Dans chaque repo GitHub de site |

---

*Dernière mise à jour : 19 avril 2026*
*Ce fichier doit être consulté et mis à jour à chaque opération sur un site.*
