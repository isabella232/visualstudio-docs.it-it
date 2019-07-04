---
title: Spazio dei nomi di sincronizzazione e nome della cartella
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160757"
---
# <a name="sync-namespace-and-folder-name"></a>Spazio dei nomi di sincronizzazione e nome della cartella

Questo refactoring si applica a:

- C#

**Cosa:** sincronizzare lo spazio dei nomi con il nome della cartella.

**Quando:** si vuole ridefinire l'architettura delle parti della soluzione trascinando un file in una nuova cartella. 

**Perché?:** si vuole essere sicuri che lo spazio dei nomi rimanga aggiornato rispetto alla nuova struttura di cartelle.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nel nome dello spazio dei nomi.
2. Premere **CTRL**+ **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare **Change namespace to \<nome cartella>** (Cambia spazio dei nomi in nome cartella).

   ![Sincronizzare lo spazio dei nomi con il nome della cartella](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
