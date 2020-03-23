---
title: Mostra elementi di importazione
description: Usare Mostra elementi di importazione per espandere IntelliSense in Visual Studio per Mac.Use Show Import Items to expand IntelliSense in Visual Studio for Mac.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451510"
---
# <a name="show-import-items"></a>Mostra elementi di importazione

Visual Studio per Mac può mostrare tutti i tipi disponibili, anche se non vengono importati nel progetto, nell'elenco di completamento IntelliSense.Visual Studio for Mac can show all available types, even if they aren't imported to your project, in your IntelliSense completion list. Selezionando un elemento che non è importato, l'istruzione corretta `using` verrà aggiunta al file di origine.

![Mostra panoramica degli elementi di importazione](media/importitems-overview.gif)

## <a name="how-to-enable"></a>Abilitazione

Per attivare questa funzionalità, aprire **Preferenze** tramite**Preferenze** di **Visual Studio** > e passare a **Editor** > di testo**IntelliSense**. Selezionare la casella Mostra elementi di importazione per abilitare elementi aggiuntivi in IntelliSense.Check the box **Show import items** to enable additional items in IntelliSense.

![mostra l'opzione Importa elementi](media/show-import-items.png)

## <a name="usage"></a>Uso

Una volta attivata **l'opzione Mostra elementi**di importazione , il processo di utilizzo della funzionalità per importare un elemento è simile alle normali azioni all'interno di IntelliSense. Durante la digitazione del codice, gli elementi validi popoleranno l'elenco di completamento. Sono inclusi gli elementi che non sono ancora stati importati. Gli elementi che non vengono importati mostreranno il loro spazio dei nomi completo a destra dell'elemento, consentendo di vedere quali importazioni si sta tirando nel progetto.

![Mostra elenco elementi di importazione](media/show-import-items-list.png)

Nell'elenco IntelliSense gli spazi dei nomi vengono visualizzati accanto `using` ai membri a cui non fa attualmente riferimento un'istruzione. Se si sceglie uno di questi elementi dall'elenco, _and_ il `using` membro verrà aggiunto al codice e l'istruzione verrà aggiunta all'inizio del file. I membri dei tipi già a cui viene fatto riferimento nel codificato non mostreranno il relativo spazio dei nomi in IntelliSense.Members from types already referenced in the coded will not show their namespace in IntelliSense.

## <a name="see-also"></a>Vedere anche

- [Azioni rapide (Visual Studio in Windows)](/visualstudio/ide/quick-actions)
- [Effettuare il refactoring del codice (Visual Studio in Windows)](/visualstudio/ide/refactoring-in-visual-studio)
