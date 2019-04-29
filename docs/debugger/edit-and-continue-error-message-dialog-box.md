---
title: Modifica e continuazione finestra di messaggio di errore | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0428ecf21da525b8f77334e57547c8f10da7cdf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851645"
---
# <a name="edit-and-continue-error-message"></a>Modifica e continuazione messaggio di errore

Il **modifica e continuazione** verrà visualizzata la finestra di messaggio di errore quando esegue il debug in un linguaggio di codice che supporta la modifica e continuazione, ma modifica e continuazione non è disponibile per le modifiche al codice apportate. Il messaggio di errore fornisce una spiegazione più dettagliata. Per rispondere alla finestra di dialogo, selezionare **OK** per chiudere la finestra di dialogo e annullare il tentativo di modifica.

Motivi possibili per questo messaggio di errore includono:

- È stato effettuato un tentativo di modificare il codice di SQL Server.
- È stato effettuato un tentativo di modificare il codice ottimizzato. Potrebbe essere necessario passare da una build di rilascio a una build di debug.
- Tentativo di modificare il codice mentre è in esecuzione, invece che durante la pausa del debugger. Provare [impostando un punto di interruzione](../debugger/using-breakpoints.md)e la modifica del codice durante la pausa.
- È stato effettuato un tentativo di modificare il codice gestito quando solo il debug non gestito è abilitato. Modifica e continuazione non funziona con [debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).
- Cambiare un codice che non è supportata da modifica e continuazione nel linguaggio di programmazione. Per altre informazioni, vedere gli articoli [supportate modifiche al codice in C# ](supported-code-changes-csharp.md), [non supportate modifiche in Visual Basic modifica e continuazione](/visualstudio/debugger/supported-code-changes-csharp), e [supportate modifiche al codice C++](supported-code-changes-cpp.md).
- Tentativo di modificare il codice in un'app è collegato, invece di avviare il debug dal **Debug** menu.
- È stato effettuato un tentativo di modificare il codice durante il debug di un ripristino di emergenza. Dr. Watson.
- Tentativo di modificare il codice dopo che si verifica un'eccezione non gestita e l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.
- È stato effettuato un tentativo di modificare il codice durante il debug di un'applicazione di runtime incorporata.
- È stato effettuato un tentativo di modificare il codice gestito Usa una versione di .NET Framework precedenti a 4.5.1 con una destinazione di app a 64 bit. Per usare modifica e continuazione per .NET Framework precedenti a 4.5.1, impostare la destinazione su **x86** nel  **\<ProjectName >** > **proprietà**  >  **Compilare** della scheda **del compilatore avanzate** impostazione.
- È stato effettuato un tentativo di modificare il codice in un assembly modificato durante il debug e ricaricato.
- È stato effettuato un tentativo di modificare il codice in un assembly che non è stato caricato.
- Avvio del debug di una versione precedente di un'app, perché la versione più recente presenta errori di compilazione.

Per altre informazioni, vedere:
- [Post di blog di continuazione e modifica di C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)
- [Modifica e continuazione](../debugger/edit-and-continue.md)