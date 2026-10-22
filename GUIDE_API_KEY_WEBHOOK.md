# Guide : Configuration des APIs et Webhooks

Ce guide vous explique comment créer des clés API et configurer les webhooks pour WooNotif selon votre plateforme e-commerce (WooCommerce, Shopify, Wix).

## 👥 Qui doit lire ce guide ?

### 🏪 Propriétaires de boutiques e-commerce
Vous possédez une boutique WooCommerce, Shopify ou Wix et souhaitez recevoir des notifications push instantanées sur votre téléphone pour chaque nouvelle commande.

### 🚚 Collaborateurs et livreurs
Vous travaillez avec plusieurs boutiques e-commerce et utilisez WooNotif pour suivre les commandes en temps réel depuis votre téléphone.

**Dans les deux cas, ce guide vous guidera pas à pas pour connecter votre/vos boutique(s) à WooNotif.**

## 📋 Prérequis par plateforme

### 🛒 WooCommerce
- Boutique WooCommerce active
- Accès administrateur WordPress
- WooCommerce installé et activé

### 🛍️ Shopify
- Boutique Shopify active
- Accès administrateur Shopify
- Permissions pour créer des applications

### 🎨 Wix
- Site Wix avec boutique e-commerce
- Accès au Centre de développement Wix
- Plan Wix Business ou supérieur

## 📱 Avantages des webhooks (Optionnel mais recommandé)

Les webhooks permettent à WooNotif de recevoir des notifications push **instantanées** pour les nouvelles commandes :

- ⚡ Notifications push immédiates (pas de délai)
- 🔋 Économie de batterie (pas de vérification périodique)
- 🔔 Alertes en temps réel pour les nouvelles commandes
- 📱 Fonctionne même en arrière-plan

**Note :** Sans webhooks, l'application vérifie les nouvelles commandes toutes les 15 minutes minimum.

## 🔑 Configuration par plateforme

### 🛒 WooCommerce

#### 1. Créer des clés API

##### Étape 1 : Accéder aux paramètres API
1. Connectez-vous à votre **tableau de bord WordPress**
2. Allez dans **WooCommerce** → **Paramètres**
3. Cliquez sur l'onglet **Avancé**
4. Dans la section **REST API**, cliquez sur **Ajouter une clé**

##### Étape 2 : Configurer la clé API
Remplissez le formulaire :
- **Description** : `WooNotif Mobile App`
- **Utilisateur** : Sélectionnez votre compte administrateur
- **Permissions** : **Lecture** (suffisant pour WooNotif)

##### Étape 3 : Générer et sauvegarder
1. Cliquez sur **Générer une clé API**
2. **IMPORTANT** : Copiez immédiatement :
   - **Consumer Key** (`ck_...`)
   - **Consumer Secret** (`cs_...`)

⚠️ **Le Consumer Secret n'apparaît qu'une fois !**

##### Étape 4 : Utiliser dans WooNotif
**Saisie manuelle :**
1. Ouvrez WooNotif
2. Entrez l'URL de votre boutique
3. Collez le Consumer Key et Consumer Secret
4. Cliquez sur **Se connecter**

**Scanner QR (plus rapide) :**
1. WooCommerce affiche un QR code après génération
2. Dans WooNotif, cliquez sur **Scanner QR**
3. Scannez le code pour remplir automatiquement les champs

#### 2. Configurer les webhooks (Optionnel)

##### Étape 1 : Accéder aux webhooks
1. WordPress → **WooCommerce** → **Paramètres** → **Avancé** → **Webhooks**
2. Cliquez sur **"Ajouter un webhook"**

##### Étape 2 : Configurer le webhook
- **Nom** : `WooNotif - Nouvelles commandes`
- **Statut** : `Actif`
- **Sujet** : `Commande créée`
- **URL de livraison** : `https://webhookwoocommerce-adydmsmlpa-uc.a.run.app`
- **Version API** : `WP REST API Integration v3`

##### Étape 3 : Sauvegarder et tester
1. Cliquez sur **"Enregistrer le webhook"**
2. Passez une commande test pour vérifier les notifications

### 🛍️ Shopify

#### 1. Créer des clés API

##### Étape 1 : Accéder aux paramètres API
1. Connectez-vous à votre **admin Shopify**
2. Allez dans **Paramètres** → **Applications et canaux de vente**
3. Cliquez sur **Développer des applications**

##### Étape 2 : Créer une application personnalisée
1. Cliquez sur **"Créer une application"**
2. Donnez un nom : `WooNotif`
3. Configurez les permissions suivantes en **lecture seule** :
   - **Content** → `read_content` (pour accéder aux informations de la boutique)
   - **Orders** → `read_orders` (pour accéder aux commandes)

##### Étape 3 : Générer et sauvegarder
1. Dans **Configuration API**, générez une **clé d'API Admin**
2. Copiez la clé générée

##### Étape 4 : Utiliser dans WooNotif
1. Ouvrez WooNotif
2. Sélectionnez **Shopify** comme plateforme
3. Entrez l'URL de votre boutique (ex: `monsite.myshopify.com`)
4. Collez la **clé d'API Admin**
5. Cliquez sur **Se connecter**

#### 2. Configurer les webhooks (Optionnel)

##### Étape 1 : Accéder aux webhooks
1. Admin Shopify → **Paramètres** → **Notifications** → **Webhooks**
2. Cliquez sur **"Créer un webhook"**

##### Étape 2 : Configurer le webhook
- **Événement** : `Order creation`
- **Format** : `JSON`
- **URL** : `https://webhookwoocommerce-adydmsmlpa-uc.a.run.app`

##### Étape 3 : Sauvegarder et tester
1. Cliquez sur **"Enregistrer"**
2. Créez une commande test dans Shopify

### 🎨 Wix

#### 1. Créer des clés API

##### Étape 1 : Accéder au Centre de développement
1. Connectez-vous à votre **éditeur Wix**
2. Allez dans **Paramètres du site** → **Gestion des ventes** → **Applications et intégrations** → **Développeur** → **Centre de développement**

##### Étape 2 : Créer une application
1. Créez une nouvelle application ou utilisez une existante
2. Activez l'API **Stores** avec permissions de lecture

##### Étape 3 : Générer les tokens
1. Générez un **Access Token** avec les droits appropriés
2. Copiez :
   - **Account ID**
   - **Site ID**
   - **Access Token**

##### Étape 4 : Utiliser dans WooNotif
1. Ouvrez WooNotif
2. Sélectionnez **Wix** comme plateforme
3. Entrez l'URL de votre site Wix
4. Renseignez les trois valeurs (Account ID, Site ID, Access Token)
5. Cliquez sur **Se connecter**

#### 2. Configurer les webhooks (Optionnel)

##### Étape 1 : Accéder aux webhooks
1. Centre de développement Wix → **Webhooks**
2. Cliquez sur **"Créer un webhook"**

##### Étape 2 : Configurer le webhook
- **Événement** : `Order Placed`
- **URL du webhook** : `https://webhookwoocommerce-adydmsmlpa-uc.a.run.app`
- **Format** : `JSON`

##### Étape 3 : Sauvegarder et tester
1. Cliquez sur **"Enregistrer"**
2. Passez une commande test sur votre site Wix

## 🛡️ Sécurité et bonnes pratiques

### ✅ Règles générales

- 🔒 Utilisez toujours des permissions **Lecture seule**
- 🏷️ Donnez des noms descriptifs à vos clés/tokens
- 🔐 Utilisez HTTPS (obligatoire pour toutes les plateformes)
- 🗑️ Révoquez les accès que vous n'utilisez plus
- 👤 Créez des comptes dédiés avec permissions limitées

### ❌ À éviter absolument

- 🚫 Ne partagez jamais vos clés API/tokens
- 🚫 Ne commitez pas vos clés dans Git
- 🚫 N'utilisez pas les permissions "Écriture" si pas nécessaire
- 🚫 Ne créez pas d'accès avec permissions trop larges


## 🔄 Gérer vos accès par plateforme

### 🛒 WooCommerce
- **Voir les clés** : WooCommerce → Paramètres → Avancé → REST API
- **Révoquer** : Cliquez sur "Révoquer" à côté de la clé
- **Régénérer** : Supprimez l'ancienne et créez-en une nouvelle

### 🛍️ Shopify
- **Voir les apps** : Paramètres → Applications et canaux de vente
- **Révoquer** : Supprimez l'application ou régénérez la clé
- **Permissions** : Modifiez les accès dans la configuration de l'app

### 🎨 Wix
- **Voir les apps** : Centre de développement → Applications
- **Révoquer** : Supprimez l'application ou régénérez les tokens
- **Permissions** : Modifiez les droits API de l'application

## ❓ Dépannage par plateforme

### 🔐 Erreurs d'authentification communes

#### "Authentification échouée (401)"
**Toutes plateformes :**
- Vérifiez que les clés/tokens sont corrects (sans espaces)
- Assurez-vous que l'accès n'a pas été révoqué
- Vérifiez les permissions (doit inclure la lecture)

#### "L'URL doit utiliser HTTPS"
**Toutes plateformes :**
- Installez un certificat SSL
- Forcez HTTPS dans vos paramètres
- Let's Encrypt offre des certificats gratuits

### 🛒 WooCommerce spécifique

#### "REST API non disponible"
- Vérifiez que WooCommerce est installé et activé
- Assurez-vous d'être administrateur
- Mettez à jour WooCommerce si nécessaire

#### "QR code ne fonctionne pas"
- Vérifiez que l'URL de la boutique est correcte
- Assurez-vous que le QR code WooCommerce est au format `ck_...|cs_...`
- Utilisez la saisie manuelle en fallback

### 🛍️ Shopify spécifique

#### "API permissions insuffisantes"
- Vérifiez que l'app a les droits "read_orders"
- Régénérez la clé API Admin si nécessaire

#### "Boutique non trouvée"
- Vérifiez l'URL (doit finir par `.myshopify.com`)
- Assurez-vous que la boutique est active

### 🎨 Wix spécifique

#### "Access Token expiré"
- Régénérez un nouveau token dans le Centre de développement
- Mettez à jour les trois valeurs (Account ID, Site ID, Token)

#### "API Stores non activée"
- Activez l'API Stores dans la configuration de l'app
- Vérifiez que le plan Wix permet l'API

## 📱 Fonctionnalités WooNotif par plateforme

### 🛒 WooCommerce
- ✅ QR codes pour saisie rapide des clés API
- ✅ Support complet des webhooks
- ✅ Toutes les versions de WooCommerce

### 🛍️ Shopify
- ✅ Clés API Admin sécurisées
- ✅ Webhooks temps réel
- ✅ Support de toutes les boutiques Shopify

### 🎨 Wix
- ✅ Tokens d'accès sécurisés
- ✅ Webhooks intégrés
- ✅ Support des boutiques Wix e-commerce

## 🔗 Ressources utiles

### 🛒 WooCommerce
- [Documentation REST API](https://woocommerce.github.io/woocommerce-rest-api-docs/)
- [Guide des webhooks](https://woocommerce.com/document/webhooks/)
- [Sécurité WooCommerce](https://woocommerce.com/document/woocommerce-security/)

### 🛍️ Shopify
- [Documentation API Admin](https://shopify.dev/docs/api/admin-rest)
- [Guide des webhooks](https://shopify.dev/docs/api/admin-rest/2023-10/resources/webhook)
- [Créer une app personnalisée](https://shopify.dev/docs/apps/build/custom-apps)

### 🎨 Wix
- [Centre de développement](https://dev.wix.com/)
- [API Stores](https://dev.wix.com/docs/rest/api-reference/stores)
- [Guide des webhooks](https://dev.wix.com/docs/develop-your-site/webhooks)

## 🧪 Tester vos connexions

### WooCommerce (avec curl)
```bash
curl -u "ck_votre_cle:cs_votre_secret" \
  https://votre-boutique.com/wp-json/wc/v3/orders?per_page=1
```

### Shopify (avec curl)
```bash
curl -H "X-Shopify-Access-Token: votre_token" \
  https://votre-boutique.myshopify.com/admin/api/2023-10/orders.json?limit=1
```

### Wix (avec curl)
```bash
curl -X POST "https://www.wixapis.com/ecom/v1/orders/search" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer votre_access_token" \
  -H "wix-account-id: votre_account_id" \
  -H "wix-site-id: votre_site_id" \
  -d '{
    "query": {
      "filter": {},
      "sort": [{"fieldName": "createdDate", "order": "DESC"}],
      "paging": {"limit": 1}
    }
  }'
```

**Si vous recevez des données JSON, votre configuration fonctionne !** ✅

---

## ❓ Questions fréquentes (FAQ)

### 🤔 Puis-je utiliser WooNotif si je ne suis pas propriétaire de la boutique ?

**Oui !** Les collaborateurs et livreurs peuvent utiliser WooNotif. Demandez simplement au propriétaire de la boutique de suivre ce guide pour créer les clés API et configurer les webhooks. Une fois configuré, vous pourrez ajouter la boutique dans votre application WooNotif.

### 🔒 Mes données sont-elles sécurisées ?

**Absolument.** WooNotif utilise uniquement des permissions de **lecture** et ne peut ni modifier ni supprimer vos données. Toutes les communications sont chiffrées (HTTPS) et vos clés API sont stockées de manière sécurisée dans l'application.

### 💰 Les webhooks sont-ils payants ?

**Non.** Les webhooks sont une fonctionnalité gratuite proposée par WooCommerce, Shopify et Wix. Ils permettent simplement à WooNotif de recevoir des notifications en temps réel sans vérifications périodiques.

### 📱 Que faire si je n'arrive pas à configurer les webhooks ?

**Pas de panique !** WooNotif fonctionne parfaitement sans webhooks. L'application vérifiera automatiquement les nouvelles commandes toutes les 15 minutes. Les webhooks améliorent seulement la réactivité des notifications.

### 🔄 Puis-je connecter plusieurs boutiques ?

**Oui !** WooNotif permet de connecter autant de boutiques que vous souhaitez. Répétez simplement le processus de configuration pour chaque boutique.

### 🚫 Que faire si je change de téléphone ?

**Vos boutiques devront être reconfigurées** car les connexions aux stores sont stockées localement sur votre téléphone.

Cependant :
- ✅ Votre **statut premium** sera automatiquement restauré si vous vous connectez avec le même compte Google Play
- ✅ Vos **données utilisateur** (ID haché) sont sécurisées sur nos serveurs
- 🔄 Vous devrez **rajouter chaque boutique** manuellement sur le nouveau téléphone en répétant le processus de configuration (clé API + webhooks)

### 🆘 Je rencontre une erreur, que faire ?

1. Vérifiez que votre clé API est correcte (sans espaces)
2. Assurez-vous que votre boutique utilise HTTPS
3. Consultez la section "Dépannage par plateforme" ci-dessus
4. Testez votre connexion avec les commandes curl fournies
5. Contactez le support WooNotif si le problème persiste

---

**Besoin d'aide ?** Consultez la documentation de WooNotif ou contactez le support.

