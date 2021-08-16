---
title: Applicare le modifiche in modalità di interruzione con Modifica e continuazione | Microsoft Docs
description: Vedere come usare Modifica e continuazione per modificare il codice Visual Basic in modalità di interruzione. Esistono diversi modi per accedere alla modalità di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 46b444d7078fe3bfa103648d616128a5879a86dffe39213f494b67247222dd28
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362393"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Procedura: Applicare modifiche in modalità di interruzione con Modifica e continuazione (Visual Basic)
È possibile usare Modifica e continuazione per modificare il codice in modalità di interruzione e continuare senza interrompere e riavviare l'esecuzione.

Per le limitazioni relative all'uso di Modifica e continuazione durante il debug, vedere Modifiche al codice [supportate (C# e Visual Basic).](../debugger/supported-code-changes-csharp.md)

### <a name="to-edit-code-in-break-mode"></a>Per modificare il codice in modalità di interruzione

1. Attivare la modalità di interruzione in uno dei seguenti modi:

    - Impostare un punto di interruzione nel codice, quindi scegliere **Avvia debug** dal menu **Debug** e attendere che l'applicazione raggiunga il punto di interruzione.

         -oppure-

    - Avviare il debug, quindi scegliere **Interrompi tutto** dal menu **Debug**.

         -oppure-

    - Quando si verifica un'eccezione, scegliere **Abilita modifica** in **Assistente eccezioni**.

2. Apportare le modifiche al codice desiderate e supportate.

     Per altre informazioni, vedere [Modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Se si tenta di apportare una modifica non consentita da Modifica e continuazione, la modifica verrà contrassegnata con una riga ondulata di colore viola e nell'Elenco attività verrà indicata un'attività da eseguire. Per poter proseguire l'esecuzione del codice, è necessario annullare la modifica non valida del codice.

3. Scegliere **Continua** dal menu **Debug** per riprendere l'esecuzione.

     Il codice verrà eseguito con le modifiche incorporate nel progetto.

## <a name="see-also"></a>Vedi anche
- [Modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Modifica e continuazione (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
