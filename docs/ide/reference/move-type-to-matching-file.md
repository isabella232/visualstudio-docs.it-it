---
title: Refactoring con spostamento di un tipo in un file corrispondente
description: Spostare un tipo in un file separato con lo stesso nome. Fare clic con il pulsante destro del mouse sul tipo, scegliere Azioni rapide e refactoring e quindi Sposta il tipo in <TypeName>.cs.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927958"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactoring con spostamento di un tipo in un file corrispondente

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di spostare il tipo selezionato in un file distinto con lo stesso nome.

**Quando:** sono presenti più classi, struct, interfacce e così via nello stesso file e si vuole separarli.

**Perché:** l'inserimento di più tipi nello stesso file può rendere difficile l'individuazione di questi tipi. Con lo spostamento dei tipi in file con lo stesso nome, il codice diventa più leggibile e la navigazione più semplice.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore all'interno del nome del tipo in cui è definito. Ad esempio:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Eseguire quindi una delle operazioni seguenti:

   - Premere **CTRL** + **.**
   - Fare clic con il pulsante destro del mouse e scegliere **Azioni rapide e refactoring**

1. Scegliere **Sposta il tipo in *TypeName*.cs** dal menu, dove *TypeName* è il nome del tipo selezionato.

   Il tipo viene spostato in un nuovo file nel progetto che ha lo stesso nome del tipo.

   - C#:

      ![Risultato inline - C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Risultato inline - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
