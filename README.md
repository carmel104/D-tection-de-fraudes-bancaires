# Détection de Fraude Bancaire par Machine Learning

## 📌 Contexte

Avec la digitalisation croissante des transactions financières, les fraudes bancaires représentent un défi majeur pour les institutions financières. La détection précoce des transactions frauduleuses permet de réduire les pertes financières et d'améliorer la sécurité des systèmes de paiement.

Ce projet applique plusieurs algorithmes d'apprentissage supervisé afin d'identifier les transactions frauduleuses et de comparer leurs performances.

---

## 🎯 Objectifs

Les objectifs principaux de cette étude sont :

* Développer des modèles de détection de fraude bancaire.
* Comparer les performances de plusieurs algorithmes de classification.
* Identifier le modèle le plus performant pour la prédiction des fraudes.

---

## 📊 Données

Les données proviennent du jeu de données **PaySim**, une simulation de transactions financières mobiles basée sur des transactions réelles d'un service de mobile money utilisé dans plusieurs pays africains.

### Variable cible

* **isFraud**

  * 1 : transaction frauduleuse
  * 0 : transaction non frauduleuse

### Variables explicatives

* `step`
* `type`
* `amount`
* `oldbalanceOrg`
* `newbalanceOrig`
* `oldbalanceDest`
* `newbalanceDest`
* `isFlaggedFraud`

Des variables indicatrices supplémentaires ont été créées :

* `isCASH_OUT`
* `isTRANSFER`

---

## 🔍 Analyse Exploratoire

L'analyse exploratoire a permis de mettre en évidence :

* Un fort déséquilibre entre les classes.
* Les transactions frauduleuses concernent principalement les opérations de type :

  * CASH_OUT
  * TRANSFER
* Une forte corrélation entre :

  * `oldbalanceOrg` et `newbalanceOrig`
  * `oldbalanceDest` et `newbalanceDest`

Ces corrélations ont motivé l'utilisation d'une régression logistique Ridge afin de limiter les effets de la multicolinéarité.

---

## 🤖 Modèles utilisés

### 1. Régression Logistique Ridge

Modèle de classification binaire régularisé permettant de gérer les problèmes de multicolinéarité.

### 2. Arbre de Classification (CART)

Méthode basée sur des règles de décision hiérarchiques facilitant l'interprétation des résultats.

### 3. Random Forest

Méthode d'ensemble utilisant plusieurs arbres construits sur des échantillons bootstrap afin d'améliorer la robustesse des prédictions.

### 4. AdaBoost

Méthode de boosting qui combine plusieurs classificateurs faibles afin de construire un modèle plus performant.

---

## 📏 Métriques d'évaluation

Les performances des modèles ont été évaluées à l'aide de :

* Accuracy
* Precision
* Recall
* F1-Score
* Courbe ROC
* Aire sous la courbe (AUC)

---

## 📈 Résultats

| Modèle                  | Precision | Recall | F1-Score | Accuracy |
| ----------------------- | --------- | ------ | -------- | -------- |
| Régression logistique Ridge        | 0.89      | 0.47   | 0.62     | 0.99     |
| Arbre de Classification | 0.90      | 0.88   | 0.89     | 0.99966  |
| Random Forest           | 0.9684    | 0.7699 | 0.8578   | 0.9997   |
| AdaBoost                | 0.9034    | 0.4696 | 0.6180   | 0.9992   |

### AUC observées

* Régression Ridge : proche de 1
* Arbre de Classification : 0.95
* Random Forest : 1.00
* AdaBoost : 1.00

---

## 🏆 Conclusion

L'ensemble des modèles étudiés présente d'excellentes performances pour la détection des fraudes bancaires.

Toutefois, les meilleurs résultats ont été obtenus avec :

* **Random Forest**
* **AdaBoost**

Ces modèles présentent les meilleures capacités de discrimination selon l'AUC et les différentes métriques de classification.

Le Random Forest apparaît particulièrement intéressant grâce à son excellent compromis entre précision et rappel.

