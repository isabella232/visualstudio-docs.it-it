---
title: Modifica e continuazione (Visual C#) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Edit and Continue
- Edit and Continue [C#]
- debugging [C#], Edit and Continue
ms.assetid: 591bd1b7-ef10-4d10-817b-3f92ca4be006
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5d54673ee46c594bd1a4bea2990d3b9bbe90ce1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "73188199"
---
# <a name="edit-and-continue-visual-c"></a>Modifica e continuazione (Visual C#)
 La funzionalità Modifica e continuazione per C# consente di apportare modifiche al codice in modalità di interruzione durante il debug. Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug. In modalità di esecuzione l'editor del codice sorgente è di sola lettura.

 La modalità Modifica e continuazione supporta la maggior parte delle modifiche che è necessario apportare durante una sessione di debug, con alcune eccezioni. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 La funzionalità modifica e continuazione è supportata in UWP in Windows 10 e nelle app x86 e x64 destinate a .NET Framework 4,6 desktop o versioni successive (il .NET Framework è solo una versione desktop).

 > [!NOTE]
 > Le app e le piattaforme non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

 Nella modalità Modifica e continuazione, le modifiche supportate vengono applicate automaticamente quando si utilizza un comando di esecuzione del debugger, ad esempio **Continua**, **Passaggio** o **Imposta istruzione successiva** oppure si valuta una funzione in una finestra del debugger.

 Per altre informazioni, vedere [procedura: usare modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Scrivere ed eseguire il debug del codice XAML in esecuzione con il ricaricamento a caldo di XAML in Visual Studio](../xaml-tools/xaml-hot-reload.md)
