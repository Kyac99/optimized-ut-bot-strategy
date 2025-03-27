# Stratégie UT Bot Optimisée

Ce dépôt contient une version optimisée de la stratégie de trading UT Bot pour TradingView Pine Script. La stratégie originale a été améliorée pour réduire le drawdown et augmenter la consistance des performances.

## Optimisations Implémentées

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

## Fonctionnalités Supplémentaires

- Visualisation des indicateurs DMI et ADX directement sur le graphique
- Marqueurs visuels pour indiquer quand chaque filtre est actif
- Paramètres configurables pour l'ADX, le DMI et les heures de trading

## Comment Utiliser

1. Copiez le code du fichier `optimized_ut_bot_strategy.pine`
2. Dans TradingView, créez un nouveau script Pine et collez le code
3. Appliquez le script à votre graphique
4. Ajustez les paramètres selon vos préférences :
   - Key Value (sensibilité)
   - Périodes ATR, ADX et DMI
   - Heures de trading
   - Seuil ADX

## Gestion du Risque

La stratégie inclut une gestion du risque intégrée qui calcule la taille des positions en fonction :
- Du capital total disponible
- D'un risque de 0.1% par trade
- De la volatilité du marché (via l'ATR)

## Avantages de cette Optimisation

1. **Réduction du Drawdown** : En filtrant les trades par tendance (DMI) et force de tendance (ADX), la stratégie évite les marchés indécis ou faibles.

2. **Amélioration de la Consistance** : Le filtrage horaire permet de se concentrer sur les périodes où le marché a tendance à avoir un comportement plus prévisible.

3. **Meilleure Visualisation** : Les indicateurs et filtres sont visualisés directement sur le graphique pour une meilleure compréhension des décisions de trading.

## Notes Importantes

- Cette stratégie est conçue comme point de départ et peut nécessiter des ajustements supplémentaires en fonction de l'instrument financier et du timeframe utilisés.
- Testez toujours votre stratégie en mode backtest avant de l'utiliser en trading réel.
- Considérez l'ajout d'autres filtres comme la volatilité ou des indicateurs de momentum pour améliorer davantage les performances.
