---
title: Individuare la DLL in cui si è verificato l'arresto anomalo del programma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4432378e10590c2ba930edf0920b9146e450f96
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852074"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Procedura: individuare la DLL in cui si è verificato l'arresto anomalo del programma (C#, C++, Visual Basic, F #)

 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto. Se si verifica un arresto anomalo in una DLL esterna al programma, è possibile identificarne la posizione utilizzando la finestra **Moduli**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli

1. Annotare l'indirizzo in cui si è verificato l'arresto.

    Se l'indirizzo non viene visualizzato nel messaggio di errore, potrebbe essere necessario utilizzare metodi alternativi per identificare la DLL. Se si sospetta una DLL di sistema, è possibile [caricare i simboli](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) dai server dei simboli Microsoft durante il debug. In caso contrario, potrebbe essere necessario [creare un file dump](../debugger/using-dump-files.md) con le informazioni sull'heap. Sono disponibili vari [strumenti](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) per creare file di dump.

2. Scegliere **Finestre** dal menu **Debug**, quindi **Moduli**.

3. Nella finestra **Moduli** individuare la colonna **Indirizzo**. Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.

4. Fare clic sul pulsante **Indirizzo** nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.

5. Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.

6. Nelle colonne **Nome** e **Percorso** cercare il nome e il percorso della DLL.

## <a name="see-also"></a>Vedere anche
- [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)
- [Procedura: utilizzare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)