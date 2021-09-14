---
title: Mostra elementi di importazione
description: Usare Mostra elementi di importazione per espandere IntelliSense in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710476"
---
# <a name="show-import-items"></a>Mostra elementi di importazione

Visual Studio per Mac possibile visualizzare tutti i tipi disponibili, anche se non vengono importati nel progetto, nell'elenco di completamento IntelliSense. Selezionando un elemento che non viene importato, al file di origine verrà aggiunta `using` l'istruzione corretta.

![show import items overview](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Abilitazione

Per abilitare questa funzionalità, aprire **Preferenze** **tramite** Visual Studio  >  **preferenze** e passare a **Editor di testo**  >  **IntelliSense.** Selezionare la casella **Mostra elementi di importazione** per abilitare elementi aggiuntivi in IntelliSense.

![opzione show import items](media/show-import-items.png)

## <a name="usage"></a>Utilizzo

Dopo aver abilitato **Mostra elementi di importazione**, il processo di utilizzo della funzionalità per importare un elemento è simile alle normali azioni all'interno di IntelliSense. Durante la digitazione del codice, gli elementi validi popolano l'elenco di completamento. Sono inclusi gli elementi che non sono ancora stati importati. Gli elementi che non vengono importati mostreranno il relativo spazio dei nomi completo a destra dell'elemento, consentendo di visualizzare le importazioni di cui si sta estraendo il progetto.

![show import items list](media/show-import-items-list.png)

Nell'elenco IntelliSense gli spazi dei nomi vengono visualizzati accanto ai membri a cui non fa attualmente riferimento `using` un'istruzione . Se si sceglie uno di questi elementi dall'elenco,  il membro verrà aggiunto al codice e l'istruzione verrà aggiunta all'inizio `using` del file. I membri dei tipi a cui si fa già riferimento nel codice non mostreranno il relativo spazio dei nomi in IntelliSense.

## <a name="see-also"></a>Vedi anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
