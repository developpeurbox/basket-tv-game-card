# Basket TV Game Card

Carte Lovelace pour les capteurs de l'intégration [hass-basket-tv](https://github.com/developpeurbox/hass-basket-tv) (Betclic Élite / Pro B / NBA).

## Installation
HACS → Dépôts personnalisés → ajouter ce dépôt (catégorie *Tableau de bord*), puis recharger le navigateur.

## Configuration
```yaml
type: custom:basket-tv-game-card
entity: sensor.basket_asvel
# optionnel
footer_bg: "rgba(0,0,0,0.45)"
footer_color: "#f77f00"
```
La carte affiche les logos, la compétition, la chaîne, la date et l'heure, et un message quand aucun match n'est prévu. Si `lien_match` est renseigné, un clic ouvre la page du match.
