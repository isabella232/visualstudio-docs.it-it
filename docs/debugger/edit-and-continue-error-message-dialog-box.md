---
title: Finestra di dialogo di errore Modifica e continuazione| Microsoft Docs
description: Modifica e continuazione potrebbe segnalare che non è disponibile per le modifiche al codice. Questo articolo illustra i possibili motivi.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 28fee1e361afbd40e8ebd134dfd702beb9c2b270
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635332"
---
# <a name="edit-and-continue-error-message"></a>Messaggio di errore di Modifica e continuazione

La finestra di **messaggio** di errore Modifica e continuazione viene visualizzata quando si esegue il debug in un linguaggio del codice che supporta Modifica e continuazione, ma Modifica e continuazione non è disponibile per le modifiche apportate al codice. Il messaggio di errore fornisce una spiegazione più dettagliata. Per rispondere alla finestra di dialogo, selezionare **OK** per chiudere la finestra di dialogo e annullare il tentativo di modifica.

I possibili motivi di questo messaggio di errore includono:

- Tentativo di modificare SQL Server codice.
- Tentativo di modificare il codice ottimizzato. Potrebbe essere necessario passare da una build di versione a una build di debug.
- Tentativo di modificare il codice mentre è in esecuzione, invece di essere sospeso nel debugger. Provare a [impostare un punto di](../debugger/using-breakpoints.md)interruzione e a modificare il codice mentre è in pausa.
- Tentativo di modificare il codice gestito quando è abilitato solo il debug non gestito. Modifica e continuazione non funziona con il [debug in modalità mista.](../debugger/how-to-debug-in-mixed-mode.md)
- Modifica del codice non supportata da Modifica e continuazione nel linguaggio di programmazione. Per altre informazioni, vedere gli articoli sulle modifiche al codice supportate [in C#,](supported-code-changes-csharp.md)le modifiche non supportate [in Visual Basic Modifica](supported-code-changes-csharp.md)e continuazione e le modifiche al codice [C++ supportate.](supported-code-changes-cpp.md)
- Tentativo di modificare il codice in un'app a cui si è collegati, anziché avviare il debug dal menu **Debug.**
- Tentativo di modificare il codice durante il debug di un dump dr. Watson.
- Il tentativo di modificare il codice dopo che si verifica un'eccezione non gestita e l'opzione Rimuovere lo **stack** di chiamate in caso di eccezioni non gestite non è selezionata.
- Tentativo di modificare il codice durante il debug di un'applicazione di runtime incorporata.
- Tentativo di modificare il codice gestito usando .NET Framework versione precedente alla 4.5.1 con una destinazione app a 64 bit. Per usare Modifica e continuazione .NET Framework precedente alla 4.5.1, impostare la destinazione su **x86** nella scheda Compilazione proprietà, impostazione Compilatore **\<ProjectName>**  >    >   avanzato. 
- Tentativo di modificare il codice in un assembly modificato durante il debug e ricaricato.
- Tentativo di modificare il codice in un assembly che non è stato caricato.
- Avvio del debug di una versione precedente di un'app, perché la versione più recente contiene errori di compilazione.

Per altre informazioni, vedere:
- [Post di blog su Modifica e continuazione di C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)
- [Modifica e continuazione](../debugger/edit-and-continue.md)