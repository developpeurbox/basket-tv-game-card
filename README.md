# 🏆 **Basket TV Game Card** 📺

[![PayPal](https://img.shields.io/badge/paypal-me-blue.svg?style=for-the-badge&color=purple&logo=paypal&logoColor=ccc&link=https%3A%2F%2Fpaypal.me%2hlaissus/5)](https://paypal.me/hlaissus/5)
[![GitHub Release]( https://img.shields.io/github/v/release/developpeurbox/basket-tv-game-card?style=for-the-badge&color=blue)](https://github.com/developpeurbox/basket-tv-game-card/releases)
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge&color=blue)](https://github.com/hacs/integration)
[![Community Forum]( https://img.shields.io/badge/community-forum-brightgreen.svg?style=for-the-badge&color=pink)](https://forum.hacf.fr/)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=for-the-badge)](https://github.com/developpeurbox/basket-tv-game-card/blob/main/LICENSE)

[![HACS Action](https://github.com/developpeurbox/basket-tv-game-card/actions/workflows/hacs.yml/badge.svg?style=for-the-badge)](https://github.com/developpeurbox/basket-tv-game-card/actions/workflows/hacs.yml)  


**Carte Lovelace personnalisée pour afficher les matchs Basket TV** avec les logos des équipes, la ou les chaînes TV et l'heure du coup d'envoi.

![Exemple Footao Game Card](/doc/images/example.png "Exemple d'affichage")

🔗 **Pour la création des capteurs (sensors)**, consultez [ce dépôt](https://github.com/developpeurbox/hass-basket-tv).

---

## 📥 **Installation**

### **Via HACS (recommandé)** 🔄
1. Ajoutez ce dépôt à HACS :
   **Dépôts personnalisés** → **Ajouter un dépôt personnalisé** → `https://github.com/developpeurbox/ha-basket-tv-game-card/`

### **Ou manuellement** 🛠️
1. Téléchargez le fichier depuis [les releases](https://github.com/developpeurbox/ha-basket-tv-game-card/releases).
2. Placez-le dans le dossier `/config/www/`.

---
## 🎨 Carte `basket-tv-game-card`

Ajoutez simplement ce code dans votre configuration :

```yaml
type: custom:basket-tv-game-card
entity: sensor.basket_asvel
footer_bg: "rgba(0,0,0,0.45)"
footer_color: "#f77f00"
```

Pour afficher tous vos matchs :

```yaml
type: custom:auto-entities
card:
  type: entities
filter:
  include:
    - options:
        type: custom:basket-tv-game-card
      entity_id: sensor.basket_*
      sort:
        method: attribute
        attribute: datetime
```

### 🎨 Personnalisation

Vous pouvez personnaliser l'apparence du pied de page (*footer*) directement via les options de la carte :

* **Arrière-plan :** Modifiez `footer_bg` (accepte les formats **HEX**, **RGB** ou **RGBA**).
* **Couleur du texte :** Ajustez `footer_color` pour assurer une visibilité optimale selon votre fond.

---
## 📭 **Aucun match prévu**

Lorsque aucun match n'est trouvé pour l'équipe configurée (match passé ou calendrier vide), la carte affiche automatiquement un état simplifié : le logo de l'équipe, son nom, et un message d'information.

![Carte aucun match](/doc/images/example_no_game.png "Affichage sans match prévu")

> **Aucun match prévu prochainement** s'affiche à la place des informations de diffusion habituelles. Dès qu'un prochain match est disponible dans le capteur, la carte reprend son affichage normal automatiquement.

---
## ℹ️ Source des données

Les informations affichées par cette carte (matchs, chaînes, logos) proviennent des capteurs de l'intégration [`hass-basket-tv`](https://github.com/developpeurbox/hass-basket-tv), elle-même alimentée par les flux publics de [**tv-sports.fr**](https://tv-sports.fr/).

