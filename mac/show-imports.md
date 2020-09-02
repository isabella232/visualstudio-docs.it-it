---
title: Mostra elementi di importazione
description: Usare Mostra elementi Import per espandere IntelliSense in Visual Studio per Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451510"
---
# <a name="show-import-items"></a>Mostra elementi di importazione

Visual Studio per Mac possibile visualizzare tutti i tipi disponibili, anche se non vengono importati nel progetto, nell'elenco di completamento di IntelliSense. Selezionando un elemento che non viene importato, l' `using` istruzione corretta verrà aggiunta al file di origine.

![Mostra Panoramica elementi di importazione](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Abilitazione

Per abilitare questa funzionalità, aprire **Preferenze** tramite **Visual Studio**  >  **Preferenze** di Visual Studio e passare a **editor di testo**  >  **IntelliSense**. Selezionare la casella **Mostra elementi Import** per abilitare elementi aggiuntivi in IntelliSense.

![Mostra l'opzione Importa elementi](media/show-import-items.png)

## <a name="usage"></a>Utilizzo

Dopo aver abilitato **Mostra elementi importazione**, il processo di utilizzo della funzionalità per importare un elemento è simile alle normali azioni all'interno di IntelliSense. Durante la digitazione di codice, gli elementi validi compileranno l'elenco di completamento. Sono inclusi gli elementi che non sono ancora stati importati. Gli elementi che non vengono importati visualizzeranno lo spazio dei nomi completo a destra dell'elemento, consentendo di visualizzare le importazioni di cui si esegue il pull nel progetto.

![Mostra elenco elementi di importazione](media/show-import-items-list.png)

Nell'elenco IntelliSense gli spazi dei nomi vengono visualizzati accanto ai membri a cui non è attualmente fatto riferimento da un' `using` istruzione. Se si sceglie uno di questi elementi nell'elenco, il membro verrà aggiunto al codice _e_ l' `using` istruzione verrà aggiunta all'inizio del file. I membri dei tipi a cui è già stato fatto riferimento nel codice non visualizzeranno lo spazio dei nomi in IntelliSense.

## <a name="see-also"></a>Vedere anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
