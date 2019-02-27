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
ms.openlocfilehash: 972ad0d772eee9b876f43bc3e2fcd032d4b7e0ab
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685365"
---
# <a name="edit-and-continue-visual-c"></a>Modifica e continuazione (Visual C#)
 La funzionalità Modifica e continuazione per C# consente di apportare modifiche al codice in modalità di interruzione durante il debug. Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug. In modalità di esecuzione l'editor del codice sorgente è di sola lettura.

 La modalità Modifica e continuazione supporta la maggior parte delle modifiche che è necessario apportare durante una sessione di debug, con alcune eccezioni. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Modifica e continuazione è supportata nella piattaforma UWP in x86 e x64 App destinate a .NET Framework 4.6 e Windows 10 desktop o versioni successive (.NET Framework è solo una versione desktop).

 > [!NOTE]
 > Piattaforme e applicazioni non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

 Nella modalità Modifica e continuazione, le modifiche supportate vengono applicate automaticamente quando si utilizza un comando di esecuzione del debugger, ad esempio **Continua**, **Passaggio** o **Imposta istruzione successiva** oppure si valuta una funzione in una finestra del debugger.

 Per altre informazioni, vedere [procedura: usare modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md).

## <a name="see-also"></a>Vedere anche
- [Procedura: Usare Modifica e continuazione (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
- [Le modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md)