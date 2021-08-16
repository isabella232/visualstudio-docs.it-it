---
title: Mostra elementi di importazione
description: Usare Mostra elementi di importazione per espandere IntelliSense in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 3159eba2984049783207bcb550e08cdd277cc1c272ae0cd4814c3a87a0d3c4a5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381913"
---
# <a name="show-import-items"></a>Mostra elementi di importazione

Visual Studio per Mac visualizzare tutti i tipi disponibili, anche se non vengono importati nel progetto, nell'elenco di completamento intelliSense. Selezionando un elemento che non viene importato, l'istruzione corretta `using` verrà aggiunta al file di origine.

![Panoramica di mostra elementi di importazione](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Abilitazione

Per abilitare questa funzionalità, aprire **Preferenze** **tramite** Visual Studio preferenze e passare a Editor di  >   **testo**  >  **IntelliSense**. Selezionare la casella **Mostra elementi di importazione** per abilitare elementi aggiuntivi in IntelliSense.

![Opzione show import items](media/show-import-items.png)

## <a name="usage"></a>Utilizzo

Dopo aver abilitato **Mostra elementi di importazione,** il processo di utilizzo della funzionalità per importare un elemento è simile alle normali azioni in IntelliSense. Durante la digitazione del codice, gli elementi validi popolano l'elenco di completamento. Sono inclusi gli elementi che non sono ancora stati importati. Gli elementi che non vengono importati mostreranno il relativo spazio dei nomi completo a destra dell'elemento, consentendo di visualizzare le importazioni di cui si sta estraendo il progetto.

![mostra l'elenco di elementi di importazione](media/show-import-items-list.png)

Nell'elenco IntelliSense gli spazi dei nomi vengono visualizzati accanto ai membri a cui un'istruzione non fa attualmente `using` riferimento. Se si sceglie uno di questi elementi dall'elenco,  il membro verrà aggiunto al codice e l'istruzione verrà aggiunta all'inizio `using` del file. I membri dei tipi a cui si fa già riferimento nel codice non visualizzano il relativo spazio dei nomi in IntelliSense.

## <a name="see-also"></a>Vedi anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
