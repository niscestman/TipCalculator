# 💰 Tip Calculator (Calculateur de Pourboire)

Une application Android moderne, simple et intuitive permettant de calculer rapidement le montant d'un pourboire et de personnaliser les options de règlement. Développée entièrement avec **Kotlin** et **Jetpack Compose (Material 3)**.

---

## 📸 Aperçu & Fonctionnalités

* **Saisie dynamique de la facture** : Champ texte dédié avec clavier numérique et icône illustrative (`money`).
* **Pourcentage de pourboire sur-mesure** : Entrée libre du pourcentage souhaité (`percent`).
* **Option d'arrondi automatique** : Commutateur (`Switch`) permettant d'arrondir le pourboire à l'entier supérieur (`ceil`).
* **Formatage monétaire automatique** : Conversion et affichage selon la devise du système (`NumberFormat.getCurrencyInstance()`).
* **Expérience utilisateur (UX)** :
  * Support de l'affichage **Edge-to-Edge**.
  * Défilement vertical (`verticalScroll`) pour éviter tout chevauchement lors de l'apparition du clavier.
  * Navigation fluide via le clavier (actions `Next` et `Done`).

---

## 🛠️ Stack Technique

* **Langage :** [Kotlin](https://kotlinlang.org/)
* **UI Framework :** [Jetpack Compose](https://developer.android.com/jetpack/compose) (Material 3)
* **Architecture UI :** Composables avec gestion d'état locale (`remember` & `mutableStateOf`)
* **Formatage :** `java.text.NumberFormat`

---

## 🏗️ Structure du Code

### `MainActivity.kt`

Le fichier principal contient les composants clés suivants :

| Composable / Fonction | Description |
| :--- | :--- |
| `TipTimeLayout()` | Composable racine qui gère les états (`amountInput`, `tipInput`, `roundUp`) et la mise en page globale. |
| `EditNumberField()` | Champ de saisie réutilisable configuré avec icône, libellé et options de clavier. |
| `RoundTheTipRow()` | Ligne contenant le commutateur (`Switch`) pour activer/désactiver l'arrondi. |
| `calculateTip()` | Fonction utilitaire privée qui effectue le calcul mathématique et le formatage monétaire. |

---

## 💻 Extrait de Code : Logique de Calcul

```kotlin
private fun calculateTip(
    amount: Double, 
    tipPercent: Double = 15.0, 
    roundUp: Boolean
): String {
    var tip = tipPercent / 100 * amount
    if (roundUp) {
        tip = kotlin.math.ceil(tip)
    }
    return NumberFormat.getCurrencyInstance().format(tip)
}
