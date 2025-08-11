UART_IT_STM32 - Bibliothèque de communication série par interruption
📌 Description
Une bibliothèque légère et efficace pour gérer les communications UART via interruptions sur microcontrôleurs STM32. Particulièrement adaptée pour les projets embarqués nécessitant une communication série non-bloquante.

✨ Fonctionnalités clés
Gestion double buffer circulaire (TX/RX) pour une communication fiable

Transmission non-bloquante ne monopolise pas le CPU

Fonction printf intégrée pour un debug facile (UART_IT_Printf)

Optimisée pour les STM32 (utilise les registres HAL directement)

Buffer configurable (taille modifiable via les macros)

Gestion des erreurs (buffer plein, transmission en cours)

🛠 Utilisation typique
c
// Initialisation
UART_IT_HandleTypeDef huart1_it;
UART_IT_Init(&huart1_it, &huart1);

// Envoi de données
UART_IT_Printf(&huart1_it, "Démarrage système...\n");

// Réception
uint8_t buffer[64];
int received = UART_IT_Read(&huart1_it, buffer, sizeof(buffer));
⚙️ Configuration
Modifiez les tailles de buffer dans le header :

c
#define UART_IT_RX_BUF_SIZE 128  // Taille buffer réception
#define UART_IT_TX_BUF_SIZE 128  // Taille buffer transmission
🚀 Points forts
Efficacité mémoire : Utilisation statique des buffers (pas d'allocation dynamique)

Portabilité : Compatible famille STM32F0/F1/F4 (et autres avec adaptation mineure)

Intégration facile : Interface simple avec seulement 4 fonctions principales

Robuste : Gestion des débordements de buffer

📝 Notes d'implémentation
L'IRQHandler doit être appelé depuis votre USARTx_IRQHandler

La fonction UART_IT_Printf utilise un buffer interne de 128 octets

Le timeout de transmission doit être géré côté application si nécessaire

📊 Comparaison avec les autres méthodes
Caractéristique	IT (cette lib)	DMA	Polling
Charge CPU	Moyenne	Faible	Elevée
Complexité	Modérée	Elevée	Faible
Débit maximal	Moyen	Elevé	Faible
Taille code	Petite	Grande	Très petite
🔧 Améliorations possibles
Ajout de callbacks pour événements

Gestion des erreurs UART (parité, framing)

Version avec buffer dynamique

Support RTOS (mutex pour accès thread-safe)

📚 Exemple complet
Voir le dossier /examples pour un projet démo complet avec:

Initialisation du périphérique

Echo des données reçues

Envoi périodique de données capteurs

📄 Licence
MIT License - libre d'utilisation dans vos projets personnels et commerciaux.
