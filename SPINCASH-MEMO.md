# 📋 SPINCASH — Mémo Projet
> Dernière mise à jour : 26 mars 2026 — v0.8

---

## 🎯 Concept
**Spincash** est un outil communautaire d'accompagnement au cashback via **Ebuyclub**.
- Slogan : *"Transformez vos achats en gains"*
- Valeur : bienveillance, réciprocité, **win-win**
- Accès : **gratuit**, ouvert à tous
- Hébergement cible : **VPS personnel**
- Système **100% cashback** — aucun flux financier direct (pas de virement, pas de PayPal)

---

## 🏗️ Architecture — État v0.8

| Module | Statut |
|--------|--------|
| Tableau de bord membre | ✅ v0.8 |
| Tableau de bord admin | ✅ v0.8 |
| Bandeau news défilant | ✅ v0.8 |
| Challenge filleuls webinaire | ✅ v0.8 |
| Parrainage filleul Ebuyclub | ✅ v0.8 |
| Mode sombre / clair | ✅ v0.8 |
| Page d'accueil publique | ✅ v0.8 |
| Modal de connexion Membre / Admin | ✅ v0.8 |
| Gestion admin membres (ajout/modif/suppression/tuteurs) | ✅ v0.8 |
| Historique cagnottes avec graphiques (courbe + barres) | ✅ v0.8 |
| Bouton bascule vue Membre/Admin (prototype) | ✅ v0.8 |
| Reliquat mensuel (report automatique) | ✅ v0.8 |
| Calculateur de gains (simulateur 2 niveaux) | ✅ v0.8 |
| Guide interactif cashback (8 slides) | ✅ v0.8 |
| Page offres du jour | ✅ v0.8 |
| Vérification IA capture cagnotte (Claude Vision) | ✅ v0.8 |
| Connexion base de données VPS | 🔜 Étape 2 |
| Authentification membres | 🔜 Étape 2 |
| Envoi emails automatiques (VPS) | 🔜 Étape 2 |
| Envoi Ebuycards automatique (VPS) | 🔜 Étape 2 |
| Bandeau news modifiable par l'admin | 🔜 Étape 2 |
| FAQ dashboard | 🔜 À faire |
| Système de nouveautés (admin → membres) | ✅ v0.8 |

---

## 👤 Logique métier — Espace Membre

### Saisie mensuelle
- Fenêtre de saisie : **du 1er au 5 de chaque mois**
- Le membre saisit sa **cagnotte Ebuyclub validée** du mois

### Qualification & blocs de 20 €
- Seuil : **20 € minimum** = 1 bloc activé
- Calcul : `blocs = floor(cagnotte / 20)`
- **Reliquat** = `cagnotte % 20` → reporté automatiquement au mois suivant
- Exemple : 24 € → 1 bloc activé, 4 € de reliquat reporté

### Redistribution aux tuteurs
- **5 € d'Ebuycard par tuteur** par bloc activé
- Flux exact :
  1. Le membre vire sa cagnotte sur son **wallet Ebuycard personnel** → **+2% de cashback**
  2. Il achète **2 Ebuycards de 5 €** par **carte bleue** → **+0,5% par Ebuycard**
  3. Il coche "Je souhaite l'offrir" et saisit l'email du tuteur
  4. Le tuteur reçoit un email "votre surprise eBuyCard vous attend"
  5. ⚠️ Le tuteur **NE DOIT PAS** cliquer sur le bouton vert — lire la zone bleue
  6. Tuteur : Ebuyclub → Mes bons d'achat → Wallet → Mes cadeaux → "J'ai reçu un bon d'achat" → saisir pseudo (avant @) + code
- Secours : bon d'achat si Ebuycards indisponibles
- ❌ PayPal supprimé partout

### Tuteurs
- **Assignés par l'admin**
- 2 tuteurs par membre, avec email affiché

---

## 💡 Astuces Ebuycard — Bonus cashback (IMPORTANT)

**Source : interface officielle Ebuyclub — confirmé le 26/03/2026**

| Action | Bonus |
|--------|-------|
| Virer sa cagnotte → wallet Ebuycard | **+2% de cashback** (en 48h ouvrées) |
| Acheter ou créditer une Ebuycard (par CB ou dépôt) | **+0,5% de cashback** |
| Utiliser l'Ebuycard pour payer des bons d'achat | Pas de bonus — simple moyen de paiement |

**Flux optimisé sur un cycle de 20 € :**
Cagnotte 20 € → virement Ebuycard (+2% = +0,40 €) → achat 2 Ebuycards 5 € par CB (+0,5% = +0,05 €) → envoi tuteurs

**Répercuté dans :** guide slides 3 et 5, boîte tuteurs, récapitulatif redistribution, section parrainage ✅

---

## 🎁 Procédure réception Ebuycard cadeau — CRUCIAL

Le tuteur reçoit un email **"[prénom], votre surprise eBuyCard vous attend !"**

### ⚠️ PIÈGE — Ne pas cliquer sur le bouton vert
Le bouton vert "Je m'inscris pour ouvrir mon cadeau" créerait un **nouveau compte** — le perdre !

### ✅ Bonne procédure (zone bleue de l'email)
1. Lire la zone bleue de l'email
2. Aller dans Ebuyclub → **Mes bons d'achat → Wallet → Mes cadeaux**
3. Cliquer **"J'ai reçu un bon d'achat"**
4. Saisir le **pseudo** de l'expéditeur (partie avant le @) + le **code** de l'email
5. L'Ebuycard s'ajoute au solde

**Répercuté dans :** slide 5 du guide, boîte tuteurs vue membre ✅

---

## ⚠️ Membre déjà sur Ebuyclub — Procédure obligatoire

Si une personne à parrainer **a déjà un compte Ebuyclub** :
1. Elle doit **fermer/supprimer son compte existant**
2. Créer un **nouveau compte avec une nouvelle adresse email**
3. S'inscrire via le **lien de parrainage Spincash**

Sans cette procédure → parrainage non rattaché.

**Répercuté dans :** slide 6 du guide, formulaire parrainage vue membre ✅

---

## 🎯 Astuce recrutement — Offrir une Ebuycard

Offrir une Ebuycard de 5 € à un futur filleul pour le motiver :

| Partie | Gain |
|--------|------|
| Filleul | 5 € Ebuycard + 3 € bonus inscription = **8 €** |
| Parrain | 3 € bonus parrainage reçu → investissement réel **~2 €** |

En plus : le parrain reçoit **10% du cashback du filleul à vie**.

**Répercuté dans :** slide 6 du guide, section parrainage vue membre ✅

---

## 📣 Système de nouveautés

**Ajouté en v0.8**

L'admin peut publier une nouveauté depuis la vue admin → elle apparaît en haut du dashboard membre sous forme d'encart avec badge **NOUVEAU**.

### Fonctionnement
- **Vue Admin** — section "Publier une nouveauté" : titre + description + choix couleur (cyan, vert, jaune, orange, rose) + prévisualisation temps réel
- **Vue Membre** — encart en haut du dashboard, au-dessus du profil
- Badge **NOUVEAU** coloré selon le thème choisi par l'admin
- Le membre ferme l'encart via le bouton × — ne réapparaît plus pour lui
- Si l'admin publie une nouvelle nouveauté → badge réapparaît pour tous
- Stockage : localStorage (côté client — à migrer vers BDD VPS en étape 2)

### Cas d'usage
- Nouvelle fonctionnalité Spincash
- Astuce cashback du mois
- Rappel webinaire
- Mise à jour du guide

---



**Source : FAQ Ebuyclub — depuis le 22/11/2017**
- **3 €** dès le premier cashback validé du filleul (achat ≥ 10 € HT)
- **10% de l'ensemble des gains cashback validés à vie**

---

## 🎰 Tombola mensuelle

- **Déclenchée si la cagnotte admin ≥ 50 €**
- Pool = **20% de la cagnotte admin**
- Chaque bon d'achat = **10 €** — envoyé par email directement d'Ebuyclub (même procédure que tuteurs)
- Tirage aléatoire parmi les membres qualifiés

| Cagnotte admin | Pool | Gagnants |
|---------------|------|----------|
| 50 € (min) | 10 € | 1 |
| 100 € | 20 € | 2 |
| 150 € | 30 € | 3 |

---

## 👥 Les deux types de filleuls

### 1. Filleul Ebuyclub (parrainage direct)
- Formulaire dans l'espace membre → email envoyé avec lien affilié Ebuyclub

### 2. Filleul Spincash (webinaire)
- 1 point par mois qualifié, cumulatif
- Distribution lors des webinaires dans l'ordre du classement, ajustable
- Après attribution : compteur remis à zéro

---

## 📖 Guide interactif cashback — 8 slides validés

| Slide | Titre | Thème |
|-------|-------|-------|
| 1 | Les 3 types de cashback Ebuyclub | 🟢 Ebuyclub — Bases |
| 2 | Comprendre votre cagnotte | 🟢 Ebuyclub — Cagnotte |
| 3 | Les erreurs qui annulent le cashback + astuces bonus | 🟢 Ebuyclub — Astuces |
| 4 | Déclarer votre cagnotte dans Spincash | 🔵 Spincash — Saisie |
| 5 | Envoyer vos Ebuycards aux tuteurs + procédure réception | 🔵 Spincash — Redistribution |
| 6 | Parrainer un nouveau membre + astuce Ebuycard + avertissement | 🔵 Spincash — Parrainage |
| 7 | Participer à la tombola mensuelle | 🟡 Spincash — Tombola |
| 8 | Utiliser les offres du jour | 🟠 Spincash — Offres |

Placé en haut du dashboard membre et intégré dans la page offres.

---

## 📸 Vérification IA capture cagnotte

- Upload capture Ebuyclub → **Claude Vision** extrait le montant "Validés"
- Tolérance ±0,10 € → correspondance = qualification auto / écart = flag admin
- Clé API configurable en vue Admin (localStorage)
- Header requis : `anthropic-dangerous-direct-browser-access: true`

---

## 🔗 Intégration Ebuyclub

- **Pas d'API publique** — saisie manuelle retenue
- **Web scraping écarté** — violation probable des CGU
- **Piste future** : partenariat Plebicom (information@plebicom.com)

---

## ⚖️ Points légaux

- Cashback = remise commerciale non imposable ✅
- Ebuycards tuteurs = contrepartie de tutorat à formaliser dans CGU
- Parrainage à deux niveaux = légal en France (art. L121-15 Code de la consommation) — pas une vente pyramidale car gains basés sur achats réels, pas recrutement
- Ne pas mentionner "propulsé par Ebuyclub" (pas de partenariat officiel)

---

## 🎨 Identité visuelle

| Élément | Valeur |
|---------|--------|
| Police titre | Bebas Neue |
| Police corps | Nunito |
| Mode sombre fond | `#111111` |
| Header | `#1a1a1a` |
| Tuiles S P I N | rouge, bleu, vert, jaune |
| Tuiles C A S H | orange, magenta, cyan, vert |
| Accent | Jaune `#f5e642` |

---

## 📁 Fichiers produits

| Fichier | Description |
|---------|-------------|
| `spincash-accueil.html` | Page d'accueil publique v0.8 |
| `spincash-dashboard.html` | Dashboard membre + admin v0.8 |
| `spincash-offres.html` | Page offres du jour v0.8 |
| `SPINCASH-MEMO.md` | Ce mémo v0.8 |

---

## 📌 Backlog

### ⚖️ Légal (priorité avant lancement)
- [ ] Vérifier la conformité fiscale (cashback tuteurs, tombola) — consulter comptable ou rescrit fiscal
- [ ] Rédiger les CGU : contrepartie tutorat + parrainage 2 niveaux légal + consentement RGPD analyse capture
- [ ] Rédiger les Mentions légales (éditeur, hébergeur VPS, RGPD)
- [ ] Créer la page Contact
- [ ] Notifier les membres du point fiscal

### 🛠️ Technique
- [ ] FAQ dashboard (questions fréquentes membres)
- [ ] Bandeau news modifiable par l'admin
- [ ] Connexion VPS — base de données réelle (MySQL/SQLite)
- [ ] Authentification membres (remplacera le bouton bascule prototype)
- [ ] Scripts VPS : emails SMTP, envoi Ebuycards, relevés PDF
- [ ] Claude Vision côté VPS (actuellement côté client)
- [ ] Notifications / rappels automatiques

---

## 🗓️ Historique des versions

### v0.8 — 26 mars 2026
- Système de nouveautés admin → membres (encart + badge NOUVEAU, fermeture par clic)
- Guide intégré en haut du dashboard membre et dans la page offres
- Astuces Ebuycard (+2%, +0,5%) répercutées partout
- Avertissement membre déjà sur Ebuyclub ajouté
- Procédure réception Ebuycard cadeau documentée
- Astuce recrutement Ebuycard 5 € archivée
- Note légale parrainage 2 niveaux dans le calculateur
- Calculateur de gains avec projection 12 mois
- Page offres du jour avec 19 offres, filtres, recherche
- Vérification IA capture cagnotte (Claude Vision)

### v0.7 — 26 mars 2026
- Gestion admin membres complète
- Historique cagnottes avec graphiques
- Logique blocs de 20 € + reliquat
- Ebuycard prioritaire + bon d'achat secours
- PayPal supprimé

### v0.1 à v0.6
- Dashboard membre + admin, données simulées
- Header, responsive, mode sombre/clair
- Logique métier redistribution, tombola, challenge filleuls
- Bandeau news, parrainage, page d'accueil
