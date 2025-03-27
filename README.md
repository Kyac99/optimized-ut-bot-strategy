# Stratégie UT Bot Optimisée

Ce dépôt contient plusieurs versions optimisées de la stratégie de trading UT Bot pour TradingView Pine Script. La stratégie originale a été améliorée pour réduire le drawdown et augmenter la consistance des performances.

## Versions Disponibles

1. **`optimized_ut_bot_strategy.pine`** - Version de base avec filtrage DMI/ADX et horaire.
2. **`optimized_ut_bot_strategy_advanced_exits.pine`** - Version avancée avec gestion améliorée des sorties et des stops.

## Optimisations de Base Implémentées

### 1. Filtrage Horaire
La stratégie ne prend désormais des positions qu'entre 8h et 20h, ce qui permet d'éviter les périodes de faible liquidité et de volatilité potentiellement imprévisible pendant les heures hors marché.

### 2. Filtrage par DMI et ADX
Des filtres basés sur les indicateurs Directional Movement Index (DMI) et Average Directional Index (ADX) ont été ajoutés pour améliorer la qualité des signaux :

- Pour les positions longues : 
  - ADX > 15 (force de la tendance significative)
  - DMI+ > DMI- (tendance haussière)
  
- Pour les positions courtes :
  - ADX > 15 (force de la tendance significative)
  - DMI- > DMI+ (tendance baissière)

## Gestion Avancée des Sorties (Version Avancée)

Notre version avancée inclut plusieurs améliorations critiques pour la gestion des sorties :

### 1. Correction des Stops Loss
Un problème a été identifié avec les stops loss qui ne se déclenchaient pas de manière fiable. Les améliorations suivantes ont été implémentées :

- Vérification forcée des stops loss à chaque barre
- Mise en œuvre d'une double logique de sortie (stratégie native + vérification manuelle)
- Visualisation améliorée des niveaux de stop loss sur le graphique

### 2. Prise de Profit Automatique
Le système clôture automatiquement les positions lorsque les profits latents atteignent 3 fois la taille du stop loss. Cela permet de :

- Sécuriser les profits significatifs
- Réduire le risque de retournement des positions profitables
- Améliorer le ratio risque/récompense global

### 3. Déplacement au Break Even (BE)
Dès que les profits latents atteignent 2 fois la taille du stop loss, le stop est automatiquement déplacé au point d'entrée (break even), ce qui :

- Élimine le risque de perte sur les trades bien engagés
- Maintient la possibilité de capture des tendances
- Améliore le ratio de gain moyen en réduisant les pertes

### 4. Visualisation des Niveaux de Trading
La version avancée affiche clairement sur le graphique :

- Les niveaux d'entrée
- Les stops loss actuels (avec ajustement au BE quand applicable)
- Les niveaux de take profit
- Des marqueurs visuels pour les événements de trading (BE atteint, TP atteint, SL déclenché)

## Fonctionnalités Communes

- Visualisation des indicateurs DMI et ADX directement sur le graphique
- Marqueurs visuels pour indiquer quand chaque filtre est actif
- Paramètres configurables pour l'ADX, le DMI et les heures de trading

## Comment Utiliser

1. Choisissez la version qui correspond le mieux à vos besoins
2. Copiez le code du fichier Pine Script correspondant
3. Dans TradingView, créez un nouveau script Pine et collez le code
4. Appliquez le script à votre graphique
5. Ajustez les paramètres selon vos préférences

## Paramètres Clés (Version Avancée)

- **Take Profit Multiplier** : Multiplicateur pour le niveau de prise de profit (par défaut : 3x la taille du stop ATR)
- **Break Even Level Multiplier** : Multiplicateur pour le niveau de passage au break even (par défaut : 2x la taille du stop ATR)
- **Key Value** : Modifie la sensibilité globale de la stratégie
- **Périodes ATR, ADX et DMI** : Ajustez selon la volatilité et le timeframe
- **Heures de trading** : Personnalisez selon votre marché et fuseau horaire

## Gestion du Risque

La stratégie inclut une gestion du risque intégrée qui calcule la taille des positions en fonction :
- Du capital total disponible
- D'un risque de 0.1% par trade
- De la volatilité du marché (via l'ATR)

## Notes Importantes

- Cette stratégie est conçue comme point de départ et peut nécessiter des ajustements supplémentaires en fonction de l'instrument financier et du timeframe utilisés.
- Testez toujours votre stratégie en mode backtest avant de l'utiliser en trading réel.
- La version avancée utilise plus de ressources de calcul mais offre une gestion du risque nettement améliorée.
- Considérez l'ajout d'autres filtres comme la volatilité ou des indicateurs de momentum pour améliorer davantage les performances.
