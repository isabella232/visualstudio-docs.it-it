---
title: Applicare le modifiche in modalità di interruzioni con modifica e continuazione | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05340b4922262eb134aca8fef4bf215342e5a997
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734025"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Procedura: applicare modifiche in modalità di interruzioni con modifica e continuazione (Visual Basic)
È possibile usare Modifica e continuazione per modificare il codice in modalità di interruzione e continuare senza interrompere e riavviare l'esecuzione.

Per le limitazioni sull'uso di modifica e continuazione durante il debug, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Per modificare il codice in modalità di interruzione

1. Attivare la modalità di interruzione in uno dei seguenti modi:

    - Impostare un punto di interruzione nel codice, quindi scegliere **Avvia debug** dal menu **Debug** e attendere che l'applicazione raggiunga il punto di interruzione.

         oppure

    - Avviare il debug, quindi scegliere **Interrompi tutto** dal menu **Debug**.

         oppure

    - Quando si verifica un'eccezione, scegliere **Attiva modifica** in informazioni sulle **eccezioni**.

2. Apportare le modifiche al codice desiderate e supportate.

     Per ulteriori informazioni, vedere [modifiche al codice supportateC# (e Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Se si tenta di apportare una modifica non consentita da Modifica e continuazione, la modifica verrà contrassegnata con una riga ondulata di colore viola e nell'Elenco attività verrà indicata un'attività da eseguire. Per poter proseguire l'esecuzione del codice, è necessario annullare la modifica non valida del codice.

3. Scegliere **Continua** dal menu **Debug** per riprendere l'esecuzione.

     Il codice verrà eseguito con le modifiche incorporate nel progetto.

## <a name="see-also"></a>Vedere anche
- [Modifiche al codice supportateC# (e Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Modifica e continuazione (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
