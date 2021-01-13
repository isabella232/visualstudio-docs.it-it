---
title: Usare modifica e continuazione (C#) | Microsoft Docs
description: Usare modifica e continuazione per apportare e applicare modifiche al codice in modalità di interruzione durante il debug, senza arrestare e riavviare la sessione di debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a0f8126689c0874c984a679da9b6debcb66a3075
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150652"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: utilizzare Modifica e continuazione (C#)
Con modifica e continuazione è possibile apportare e applicare modifiche al codice in modalità di interruzione durante il debug, senza dover arrestare e riavviare la sessione di debug.

La funzionalità modifica e continuazione per C# viene eseguita automaticamente quando si apportano modifiche al codice in modalità di interruzione, quindi si continua a eseguire il debug utilizzando l'istruzione **continue**, **Step** o **set Next** oppure si valuta una funzione in una finestra del debugger.

Per altre informazioni, vedere [modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>La funzionalità modifica e continuazione non è supportata per il codice di integrazione ottimizzato, misto o SQL Server Common Language Runtime (CLR). Per informazioni su altri scenari non supportati, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md). Se si tenta di modificare e continuare con uno di questi scenari, viene visualizzata una finestra di messaggio che informa che la funzionalità modifica e continuazione non è supportata.

**Per abilitare o disabilitare modifica e continuazione:**

1. Se ci si trova in una sessione di debug, arrestare il debug (**debug**  >  **Interrompi debug** o **MAIUSC** + **F5**).

1. In **strumenti**  >  **Opzioni** (o   >  **Opzioni** di debug) > **debug**  >  **generale** selezionare o deselezionare la casella di controllo **Abilita modifica e continuazione** .

L'impostazione viene applicata quando si avvia o si riavvia la sessione di debug.

**Per utilizzare modifica e continuazione:**

1. Durante il debug, in modalità di interruzioni, apportare una modifica al codice sorgente.

1. Dal menu **debug** , fare clic su **continua**, **Esegui** **istruzione o imposta istruzione successiva** oppure valutare una funzione in una finestra del debugger.

   Il debug continua con il nuovo codice compilato.

Alcuni tipi di modifiche al codice non sono supportati da modifica e continuazione. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).
