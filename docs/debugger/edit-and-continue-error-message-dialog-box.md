---
title: Finestra di dialogo modifica e continuazione messaggio di errore | Microsoft Docs
description: Modifica e continuazione può indicare che non è disponibile per le modifiche del codice. Questo articolo fornisce le possibili cause.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ef34889b838e2f7eaa92420eec90db9def57e65
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96862845"
---
# <a name="edit-and-continue-error-message"></a>Messaggio di errore di modifica e continuazione

La finestra di messaggio di errore di **modifica e continuazione** viene visualizzata quando si esegue il debug in un linguaggio del codice che supporta modifica e continuazione, ma la funzionalità modifica e continuazione non è disponibile per le modifiche del codice apportate. Il messaggio di errore fornisce una spiegazione più dettagliata. Per rispondere alla finestra di dialogo, fare clic su **OK** per chiudere la finestra di dialogo e annullare il tentativo di modifica.

I possibili motivi di questo messaggio di errore includono:

- Tentativo di modificare il codice SQL Server.
- Tentativo di modificare il codice ottimizzato. Potrebbe essere necessario passare da una build di rilascio a una build di debug.
- Tentativo di modificare il codice mentre è in esecuzione, anziché mentre è in pausa nel debugger. Provare [a impostare un](../debugger/using-breakpoints.md)punto di interruzione e a modificare il codice mentre è in pausa.
- Tentativo di modificare il codice gestito quando è abilitato solo il debug non gestito. Modifica e continuazione non funziona con il [debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).
- Apportare una modifica al codice non supportata da modifica e continuazione nel linguaggio di programmazione. Per ulteriori informazioni, vedere gli articoli sulle [modifiche al codice supportate in C#](supported-code-changes-csharp.md), modifiche non [supportate in Visual Basic modifica e continuazione](supported-code-changes-csharp.md)e [modifiche al codice C++ supportate](supported-code-changes-cpp.md).
- Tentativo di modificare il codice in un'app a cui si è connessi, anziché avviare il debug dal menu **debug** .
- Tentativo di modificare il codice durante il debug di un dump di Dr. Watson.
- Il tentativo di modificare il codice dopo un'eccezione non gestita si verifica e l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.
- Tentativo di modificare il codice durante il debug di un'applicazione di runtime incorporata.
- Tentativo di modificare il codice gestito usando una versione di .NET Framework precedente alla 4.5.1 con una destinazione app a 64 bit. Per usare modifica e continuazione per .NET Framework precedenti a 4.5.1, impostare la destinazione su **x86** nella **\<ProjectName>**  >  **Properties**  >  scheda **compilazione** proprietà, impostazioni **del compilatore avanzate** .
- Tentativo di modificare il codice in un assembly modificato durante il debug ed è stato ricaricato.
- Tentativo di modificare il codice in un assembly che non è stato caricato.
- Avvio del debug di una versione precedente di un'app, perché la versione più recente contiene errori di compilazione.

Per altre informazioni, vedere:
- [Post di Blog su modifica e continuazione di C++](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)
- [Modifica e continuazione](../debugger/edit-and-continue.md)