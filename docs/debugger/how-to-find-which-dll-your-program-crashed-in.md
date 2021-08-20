---
title: Individuare la DLL in cui si è | Microsoft Docs
description: Usare la finestra Moduli per identificare la DLL esterna attiva quando l'applicazione si arresta in modo anomalo. È possibile eseguire questa operazione per una DLL di sistema o per il codice di un altro utente.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d4336c741aac8eded2ce529f5a3fa57dd5abf1d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128364"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Procedura: Trovare la DLL in cui si è arrestato il programma (C#, C++, Visual Basic, F#)

 Se l'applicazione si arresta in modo anomalo durante la chiamata a una DLL di sistema o al codice di un altro utente, è necessario identificare la DLL attiva al momento dell'arresto. Se si verifica un arresto anomalo in una DLL esterna al programma, è possibile identificarne la posizione utilizzando la finestra **Moduli**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Per stabilire la posizione in cui si è verificato un arresto anomalo mediante la finestra Moduli

1. Annotare l'indirizzo in cui si è verificato l'arresto.

    Se l'indirizzo non viene visualizzato nel messaggio di errore, potrebbe essere necessario usare metodi alternativi per identificare la DLL. Se si sospetta una DLL di sistema, è possibile [caricare i](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) simboli dai server di simboli Microsoft durante il debug. In caso contrario, potrebbe essere necessario [creare un file dump](../debugger/using-dump-files.md) con informazioni sull'heap. Sono [disponibili vari](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) strumenti per creare file di dump.

2. Scegliere **Finestre** dal menu **Debug**, quindi **Moduli**.

3. Nella finestra **Moduli** individuare la colonna **Indirizzo**. Per visualizzarla potrebbe essere necessario utilizzare la barra di scorrimento.

4. Fare clic sul pulsante **Indirizzo** nella parte superiore della colonna per ordinare le DLL in base all'indirizzo.

5. Cercare nell'elenco ordinato la DLL il cui intervallo di indirizzi contenga la posizione in cui si è verificato l'arresto anomalo.

6. Nelle colonne **Nome** e **Percorso** cercare il nome e il percorso della DLL.

## <a name="see-also"></a>Vedi anche
- [Debug di progetti di DLL](../debugger/debugging-dll-projects.md)
- [Procedura: utilizzare la finestra Moduli](../debugger/how-to-use-the-modules-window.md)