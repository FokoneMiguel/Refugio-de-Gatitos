# 📖 GUIDE COMPLET — Hogar de Gatitos
## Ton site web professionnel expliqué étape par étape

---

## 📋 TABLE DES MATIÈRES

1. [Les informations dont j'ai besoin de toi](#info)
2. [Configurer le formulaire de contact (recevoir des emails)](#emailjs)
3. [Configurer le bouton WhatsApp](#whatsapp)
4. [Ajouter tes propres photos de chatons par race](#photos)
5. [Changer les textes et les prix](#textes)
6. [Publier le site sur Internet](#publier)
7. [Faire de la publicité sur Google Ads](#googleads)
8. [Conseils pro supplémentaires](#pro)

---

## 1. 📝 LES INFORMATIONS DONT J'AI BESOIN {#info}

Pour que le site fonctionne à 100 %, prépare ces informations :

| Information | Exemple | Où c'est utilisé |
|---|---|---|
| **Ton numéro WhatsApp** (avec l'indicatif pays) | +34 607 36 05 29 | Bouton WhatsApp |
| **Ton email de réception** | moncriadero@gmail.com | Formulaire de contact |
| **Nom exact de ton criadero** | Hogar de Gatitos | Logo, titre, SEO |
| **Tes propres photos de chatons** | .jpg ou .png, min. 800px | Cartes des races |
| **Tes prix par race** | Desde 900 € | Cartes des races |

---

## 2. 📧 CONFIGURER LE FORMULAIRE (RECEVOIR DES EMAILS) {#emailjs}

On utilise **EmailJS** — c'est **gratuit jusqu'à 200 emails/mois** et ça ne nécessite aucun serveur ni programmation avancée.

### Étape 1 — Créer un compte gratuit

1. Va sur **https://www.emailjs.com**
2. Clique sur **"Sign Up Free"**
3. Inscris-toi avec l'email où tu veux recevoir les messages des clients

### Étape 2 — Connecter ton email

1. Dans le tableau de bord EmailJS, clique sur **"Email Services"** à gauche
2. Clique sur **"Add New Service"**
3. Choisis **Gmail** (ou ton fournisseur email)
4. Clique sur **"Connect Account"** → autorise avec Google
5. **Note bien le "Service ID"** qui s'affiche (exemple : `service_abc123`)

### Étape 3 — Créer le modèle d'email

1. Dans le menu gauche, va sur **"Email Templates"**
2. Clique sur **"Create New Template"**
3. Configure le modèle comme ceci :

**Champ "To Email"** → ton adresse email

**Champ "Subject"** :
```
🐱 Nouvelle demande d'adoption — {{from_name}}
```

**Champ "Content"** (corps du message) :
```
━━━━━━━━━━━━━━━━━━━━━━━
NOUVELLE DEMANDE D'ADOPTION
━━━━━━━━━━━━━━━━━━━━━━━

👤 Nom complet :   {{from_name}}
📧 Email :         {{from_email}}
📞 Téléphone :     {{phone}}
🐱 Race souhaitée: {{breed}}

💬 Message :
{{message}}

━━━━━━━━━━━━━━━━━━━━━━━
Réponds directement à cet email
ou contacte le client à : {{reply_to}}
```

4. Clique sur **"Save"**
5. **Note le "Template ID"** (exemple : `template_xyz789`)

### Étape 4 — Récupérer ta clé publique

1. Dans le menu, va sur **"Account"** → onglet **"General"**
2. Copie ta **"Public Key"** (exemple : `abcDEF123ghiJKL`)

### Étape 5 — Coller les clés dans le site

Ouvre le fichier `hogar-gatitos-v3.html` dans un éditeur de texte (Bloc-notes, Notepad++ ou VS Code).

Cherche ces 3 lignes en haut du JavaScript :

```javascript
const EMAILJS_SERVICE_ID  = 'TU_SERVICE_ID';
const EMAILJS_TEMPLATE_ID = 'TU_TEMPLATE_ID';
const EMAILJS_PUBLIC_KEY  = 'TU_PUBLIC_KEY';
```

Remplace chaque valeur par la tienne, par exemple :

```javascript
const EMAILJS_SERVICE_ID  = 'service_abc123';
const EMAILJS_TEMPLATE_ID = 'template_xyz789';
const EMAILJS_PUBLIC_KEY  = 'abcDEF123ghiJKL';
```

Enregistre le fichier.

### ✅ Tester le formulaire

Remplis le formulaire sur ton site → tu devrais recevoir l'email en quelques secondes.

> 💡 **Conseil pro** : Crée un email dédié comme `contacto@hogardegatitos.es`
> pour séparer les demandes d'adoption de tes emails personnels.

---

## 3. 📱 CONFIGURER LE BOUTON WHATSAPP {#whatsapp}

### Où changer ton numéro

Dans le fichier HTML, cherche cette ligne (vers le début) :

```html
<a href="https://wa.me/TU_NUMERO_WHATSAPP?text=Hola...
```

Remplace `TU_NUMERO_WHATSAPP` par ton numéro **sans espaces, sans le signe +** :

| Ton numéro réel | Ce que tu écris dans le code |
|---|---|
| +34 607 36 05 29 | `34607360529` |
| +33 6 12 34 56 78 | `33612345678` |
| +237 691 23 45 67 | `237691234567` |

### Personnaliser le message automatique

Quand un client clique sur le bouton, WhatsApp s'ouvre avec un message pré-écrit. Tu peux le changer.

Le message actuel dans le code :
```
Hola%2C%20me%20interesa%20adoptar%20un%20gatito.%20%C2%BFPodr%C3%ADa%20darme%20m%C3%A1s%20informaci%C3%B3n%3F
```
Cela correspond à : *"Hola, me interesa adoptar un gatito. ¿Podría darme más información?"*

Pour écrire ton propre message :
1. Va sur **https://www.urlencoder.org**
2. Tape ton message en español dans la zone de texte
3. Clique sur "Encode"
4. Copie le résultat et remplace la partie après `?text=` dans le code

---

## 4. 🐱 AJOUTER TES PHOTOS DE CHATONS PAR RACE {#photos}

### Option A — Hébergement d'images gratuit (recommandé)

1. Crée un compte gratuit sur **https://cloudinary.com**
2. Clique sur "Upload" et envoie tes photos
3. Une fois uploadée, clique sur la photo → copie le **"URL"** qui se termine par `.jpg`

### Option B — Si tu publies sur Hostinger

Si tu mets le site sur Hostinger (voir section 6), tu peux créer un dossier `images/` à côté de ton fichier HTML et utiliser des chemins relatifs comme `images/maine-coon.jpg`.

### Comment remplacer une photo dans le code

Dans le fichier HTML, cherche les commentaires marqués `👉`. Par exemple pour le Maine Coon :

```html
<!-- 👉 Remplace cette URL par ta propre photo Maine Coon -->
<img src="https://images.unsplash.com/photo-xxx" alt="Maine Coon" loading="lazy">
```

Remplace l'URL complète par la tienne :

```html
<!-- 👉 Remplace cette URL par ta propre photo Maine Coon -->
<img src="https://res.cloudinary.com/toncompte/image/upload/maine-coon.jpg" alt="Maine Coon" loading="lazy">
```

### Conseils pour de belles photos

| Critère | Recommandé |
|---|---|
| **Format** | .jpg (plus léger) |
| **Taille minimale** | 800 × 600 px |
| **Taille maximale** | 1600 × 1200 px |
| **Poids maximum** | 400 Ko |
| **Compresser les photos** | Utilise **https://squoosh.app** (gratuit) |
| **Qualité** | Bonne lumière naturelle, chaton net, fond propre |

---

## 5. ✏️ CHANGER LES TEXTES ET PRIX {#textes}

### Changer le nom du criadero

Cherche **"Hogar de Gatitos"** dans le fichier (Ctrl+F) et remplace par ton vrai nom partout.

### Changer les prix

Cherche **"Desde"** dans le fichier :

```html
<div class="breed-price">Desde 900 €</div>
```

Modifie le montant selon ton tarif réel.

### Changer le téléphone affiché

Cherche `+34 607 36 05 29` et remplace par ton numéro.

### Changer l'email affiché dans la section contact

Cherche `TU_EMAIL@dominio.com` et remplace par ton vrai email.

### Ajouter une nouvelle race

Copie un bloc de carte existant dans le code et colle-le dans `<div class="breeds-grid" id="breedsGrid">` :

```html
<div class="breed-card" data-coat="long">  ← "long" ou "short" selon le pelage
  <div class="breed-img-wrap">
    <!-- 👉 Ton URL de photo -->
    <img src="TON_URL_PHOTO" alt="Nom de la race" loading="lazy">
    <div class="breed-overlay"></div>
    <div class="breed-tag">Exclusivo</div>  ← étiquette optionnelle
    <div class="breed-cta-overlay" data-i18n="card_cta">Ver disponibles</div>
  </div>
  <div class="breed-info">
    <div class="breed-name">Nom de la Race</div>
    <div class="breed-desc-short">Description courte…</div>
    <div class="breed-meta">
      <div class="breed-price">Desde X €</div>
      <div class="breed-avail">
        <div class="avail-dot"></div>
        <span data-i18n="available">Disponible</span>
      </div>
    </div>
  </div>
</div>
```

---

## 6. 🌐 PUBLIER LE SITE SUR INTERNET {#publier}

### Option recommandée — Hostinger (à partir de ~3 €/mois)

C'est la meilleure option si tu veux un **vrai nom de domaine professionnel**.

1. Va sur **https://www.hostinger.fr**
2. Achète un plan **"Web Starter"** + un nom de domaine (ex : `hogardegatitos.es` ou `hogardegatitos.com`)
3. Dans le tableau de bord → **"Gestionnaire de fichiers"**
4. Ouvre le dossier `public_html`
5. Supprime le fichier existant si besoin
6. **Glisse et dépose** ton fichier HTML
7. **Renomme-le en `index.html`** (très important)
8. Ton site est en ligne !

### Option gratuite — Netlify (sans nom de domaine personnalisé)

1. Va sur **https://www.netlify.com**
2. Crée un compte gratuit (avec ton email ou GitHub)
3. Sur le tableau de bord, cherche le bouton **"Deploy manually"** ou glisse ton fichier HTML dans la zone indiquée
4. Netlify te génère une URL gratuite comme `hogar-gatitos.netlify.app`

> 💡 **Conseil pro** : Pour vendre des chatons de valeur, **un vrai nom de domaine**
> comme `hogardegatitos.es` inspire bien plus confiance qu'une URL gratuite.
> Le client qui voit `.netlify.app` peut douter du sérieux du vendeur.

---

## 7. 📢 PUBLICITÉ SUR GOOGLE ADS {#googleads}

### Pourquoi Google Ads pour un criadero ?

Les personnes qui tapent "comprar gatito Maine Coon" ou "gatitos ragdoll precio" sont **prêtes à acheter**. Google Ads place ton annonce en première position pour ces recherches.

### Étape 1 — Créer un compte Google Ads

1. Va sur **https://ads.google.com**
2. Connecte-toi avec ton compte Gmail
3. Configure le pays et la devise (€)

### Étape 2 — Type de campagne à choisir

- **Type** : Réseau de Recherche (Search)
- **Objectif** : Leads / Contacts
- **Réseau** : Décocher "Réseau Display" pour commencer

### Étape 3 — Mots-clés recommandés

Copie ces mots-clés dans ta campagne :

**Mots-clés à forte intention (les plus précieux) :**
```
"comprar gatito maine coon"
"gatitos ragdoll en venta"
"gatitos de raza precio"
"criadero de gatos [ta ville]"
"adoptar gatito persa"
"gatitos british shorthair"
"gatito bengalí precio"
```

**Mots-clés négatifs (pour ne PAS dépenser d'argent dessus) :**
```
-gratis
-shelter
-rescate
-abandonado
-adopción gratuita
-youtube
```

### Étape 4 — Textes d'annonces recommandés

```
ANNONCE 1 :
Titre 1 : Gatitos de Raza Premium 🐱
Titre 2 : Maine Coon, Ragdoll, Persa y Más
Titre 3 : Garantía de Salud Incluida
Description : Criadero con 20+ años de experiencia. Todas las razas disponibles, pedigrí certificado. ¡Contáctenos hoy!

ANNONCE 2 :
Titre 1 : Compra tu Gatito con Confianza
Titre 2 : Vacunado, Desparasitado, con Pedigrí
Titre 3 : Más de 500 Familias Satisfechas
Description : 21 razas disponibles. Asesoramiento personalizado gratuito. Entrega en toda España.
```

### Étape 5 — Budget conseillé pour démarrer

| Budget journalier | Estimation clics/mois | Pour qui ? |
|---|---|---|
| 5 €/jour (150 €/mois) | 30 à 60 clics | Test initial |
| 10 €/jour (300 €/mois) | 80 à 150 clics | Croissance stable |
| 20 €/jour (600 €/mois) | 180 à 300 clics | Visibilité maximale |

> 💡 **Conseil** : Commence avec 5 €/jour pendant 2 semaines pour tester.
> Analyse quels mots-clés génèrent des contacts, puis augmente le budget sur ceux-là.

### Étape 6 — Suivre tes conversions (important)

Pour savoir quelle annonce génère vraiment des contacts :
1. Dans Google Ads → **Outils** → **Conversions** → **Nouvelle conversion**
2. Choisis **"Site Web"**
3. Sélectionne **"Envoi de formulaire"**
4. Google te donne un code à coller dans ton HTML juste avant `</head>`

### ✅ Checklist avant d'activer les annonces

- [ ] Le site est publié et se charge rapidement
- [ ] Le formulaire de contact fonctionne (test avec ton propre email)
- [ ] Le bouton WhatsApp fonctionne
- [ ] Les photos sont tes vraies photos (pas des photos de stock)
- [ ] Les prix sont à jour
- [ ] Le site s'affiche bien sur mobile (vérifie sur ton téléphone !)

---

## 8. 💎 CONSEILS PRO SUPPLÉMENTAIRES {#pro}

### SEO — Apparaître dans Google gratuitement

Ajoute ces balises juste après `<title>` dans le HTML. Cela aide Google à comprendre ton site :

```html
<meta name="description" content="Criadero premium de gatitos de raza en España. Maine Coon, Ragdoll, Persa, Bengalí. Más de 20 años de experiencia. Pedigrí certificado y garantía de salud.">
<meta property="og:title" content="Hogar de Gatitos — Criadero Premium">
<meta property="og:description" content="Gatitos de raza de excepción con pedigrí certificado.">
<meta property="og:image" content="URL_D_UNE_BELLE_PHOTO_DE_TON_CHATON">
```

### Instagram — Le réseau parfait pour les chatons

- Publie **5 à 7 photos/vidéos** par semaine
- Les **Reels** (vidéos courtes) génèrent le plus grand nombre de vues
- Hashtags à utiliser : `#gatitosderaza #mainecoon #ragdoll #gatitosenventa #criadero #gatos`
- **Mets le lien de ton site dans ta bio** Instagram
- Réponds aux messages en moins de 2 heures

### Google My Business (totalement gratuit)

1. Va sur **https://business.google.com**
2. Enregistre ton criadero comme entreprise locale
3. Ajoute tes photos, horaires et le lien de ton site
4. Les clients pourront te laisser des avis visibles directement sur Google
5. Ça améliore aussi ton référencement local gratuitement

### Répondre vite = vendre plus

Un client qui ne reçoit pas de réponse dans **les 24 heures** va voir ailleurs.

- Active les notifications email sur ton téléphone
- Installe WhatsApp Business (gratuit) pour mieux gérer les demandes
- Configure un **message automatique de bienvenue** sur WhatsApp Business

### Ajouter une FAQ à ton site (très efficace)

Une section Questions Fréquentes rassure les acheteurs. Voici les questions à inclure :

- À quel âge les chatons sont-ils livrés ?
- Quels documents sont fournis à l'adoption ?
- Livrez-vous dans toute l'Espagne / l'Europe ?
- Comment se passe le paiement ?
- Puis-je visiter le criadero ?

### Formulaire de réservation

Pour les clients sérieux, tu peux demander un acompte pour "réserver" un chaton. Ajoute une ligne dans ton formulaire : *"Je souhaite réserver — je suis prêt à verser un acompte de X €"*

---

## 🔧 RÉCAPITULATIF DES 4 MODIFICATIONS À FAIRE

| Ce qu'il faut remplacer | Où dans le fichier HTML |
|---|---|
| `TU_NUMERO_WHATSAPP` | Dans le bouton WhatsApp (ex: `34607360529`) |
| `TU_EMAIL@dominio.com` | Dans la section contact |
| `TU_SERVICE_ID` / `TU_TEMPLATE_ID` / `TU_PUBLIC_KEY` | 3 lignes JavaScript en haut du `<script>` |
| Les URLs des photos avec `👉` | Dans chaque carte de race |

---

## 🆘 BESOIN D'AIDE ?

Si tu bloques sur une étape, reviens poser ta question précise à Claude avec le détail du problème. Garde ce document en lieu sûr.

---

*Document généré pour : Hogar de Gatitos | Version 3.0 — Site Responsive*
