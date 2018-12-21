---
title: Refactoring con spostamento di un tipo in un file corrispondente
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059639"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactoring con spostamento di un tipo in un file corrispondente

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di spostare il tipo selezionato in un file distinto con lo stesso nome.

**Quando:** sono presenti più classi, struct, interfacce e così via nello stesso file e si vuole separarli.

**Perché?:** l'inserimento di più tipi nello stesso file può rendere difficile l'individuazione di questi tipi. Con lo spostamento dei tipi in file con lo stesso nome, il codice diventa più leggibile e la navigazione più semplice.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore all'interno del nome del tipo in cui è definito. Ad esempio:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL**+**.**
   - Fare clic con il pulsante destro del mouse e scegliere **Azioni rapide e refactoring**

1. Scegliere **Sposta il tipo in *TypeName*.cs** dal menu, dove *TypeName* è il nome del tipo selezionato.

   Il tipo viene spostato in un nuovo file nel progetto che ha lo stesso nome del tipo.

   - C#:

      ![Risultato inline - C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Risultato inline - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
