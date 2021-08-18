---
title: Rinominare un file in modo che corrisponda a un tipo
description: Informazioni su come usare il menu Azioni rapide e refactoring per rinominare un tipo in modo che corrisponda al nome del file o rinominare un nome file in modo che corrisponda al tipo in esso contenuto.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 9202adea6b129e3e747426fbb6f0694bfd23c250
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048713"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refactoring con sincronizzazione di un tipo con un nome di file o un nome di file con un tipo

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** consente di rinominare un tipo in modo che corrisponda al nome del file oppure di rinominare un file in modo che corrisponda al tipo che contiene.

**Quando:** è stato rinominato un file o un tipo e non è ancora stato aggiornato il file o il nome corrispondente.

**Perché:** se si inserisce un tipo in un file con un nome diverso o viceversa, risulta difficile trovare ciò che si sta cercando. Rinominando il tipo o il file, il codice diventa più leggibile e la navigazione più semplice.

> [!NOTE]
> Questo refactoring non è ancora disponibile per i progetti .NET Standard e .NET Core.

## <a name="how-to"></a>Procedure

1. Evidenziare o posizionare il cursore del testo all'interno del nome del tipo da sincronizzare:

   - C#:

       ![Codice evidenziato - C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato - Visual Basic](media/synctype-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rinomina file in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.
      - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Rinomina tipo in _NomeFile_** dal popup della finestra di anteprima, dove *NomeFile* è il nome del file corrente.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Rinomina file in *NomeTipo*.cs** dal popup della finestra di anteprima, dove *NomeTipo* è il nome del tipo selezionato.
      - Fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Rinomina tipo in _NomeFile_** dal popup della finestra di anteprima, dove *NomeFile* è il nome del file corrente.

   Il tipo o il file viene rinominato.

   - C#: nell'esempio seguente il file **MyClass.cs** è stato rinominato in **MyNewClass.cs** in modo che corrisponda al nome del tipo.

       ![Risultato inline C#](media/synctype-result-cs.png)

   - Visual Basic: nell'esempio seguente il file **Employee.vb** è stato rinominato in **Person.vb** in modo che corrisponda al nome del tipo.

       ![Risultato inline Visual Basic](media/synctype-result-vb.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
