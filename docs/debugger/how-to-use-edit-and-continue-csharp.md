---
title: Usare Modifica e continuazione (C#) | Microsoft Docs
description: Usare Modifica e continuazione per apportare e applicare modifiche al codice in modalità di interruzione durante il debug, senza arrestare e riavviare la sessione di debug in Visual Studio.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 0c0c96fa5158d46d0a8ceafa027c393acb7c94c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128039"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: utilizzare Modifica e continuazione (C#)
Con Modifica e continuazione è possibile apportare e applicare modifiche al codice in modalità di interruzione durante il debug, senza dover arrestare e riavviare la sessione di debug.

Modifica e continuazione per C# viene eseguito automaticamente quando si apportano modifiche al codice in modalità di interruzione, quindi si continua il debug usando **Continua** **,** Passaggio o Imposta istruzione successiva **oppure** si valuta una funzione in una finestra del debugger.

Per altre informazioni, vedere [Modifica e continuazione (Visual C#).](../debugger/edit-and-continue-visual-csharp.md)

>[!NOTE]
>Modifica e continuazione non è supportato per il codice di integrazione ottimizzato, misto o SQL Server di integrazione CLR (Common Language Runtime). Per informazioni su altri scenari non supportati, vedere [Modifiche al codice supportate (C# e Visual Basic).](../debugger/supported-code-changes-csharp.md) Se si tenta di modificare e continuare con uno di questi scenari, viene visualizzata una finestra di messaggio che indica che Modifica e continuazione non è supportato.

**Per abilitare o disabilitare Modifica e continuazione:**

1. Se si è in una sessione di debug, arrestare il debug (**Debug**  >  **Arresta** debug o **MAIUSC** + **F5).**

1. In **Opzioni**  >  **degli strumenti** (o Opzioni di **debug**) >  >   **Debug**  >  **Generale** selezionare  o deselezionare la casella di controllo Abilita Modifica e continuazione .

L'impostazione viene attivata all'avvio o al riavvio della sessione di debug.

**Per usare Modifica e continuazione:**

1. Durante il debug, in modalità di interruzione, apportare una modifica al codice sorgente.

1. Scegliere **Continua** dal menu Debug **,** Esegui **istruzione** o Imposta istruzione **successiva** oppure valutare una funzione in una finestra del debugger.

   Il debug continua con il nuovo codice compilato.

Alcuni tipi di modifiche al codice non sono supportati da Modifica e continuazione. Per altre informazioni, vedere [Modifiche al codice supportate (C# e Visual Basic).](../debugger/supported-code-changes-csharp.md)
