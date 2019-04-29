---
title: Modifica e continuazione (Visual Basic) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f73b67ac4268c04dfa9ff7ab020891623f528f9b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851263"
---
# <a name="edit-and-continue-visual-basic"></a>Modifica e continuazione (Visual Basic)
Modifica e continuazione è una funzionalità per il debug di [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] che consente di apportare modifiche al codice mentre viene eseguito in modalità di interruzione. Dopo aver applicato le modifiche al codice, è possibile riprendere l'esecuzione del codice con le nuove modifiche già inserite e verificarne l'effetto.

 La funzionalità Modifica e continuazione può essere utilizzata ogni volta che si attiva la modalità di interruzione. Punta alla riga che contiene un'istruzione eseguibile in un corpo del metodo o proprietà che verrà eseguito in modalità di interruzione, il puntatore all'istruzione, ovvero la freccia gialla nella finestra di origine, successivo.

 La modalità Modifica e continuazione supporta la maggior parte delle modifiche che è necessario apportare durante una sessione di debug, con alcune eccezioni. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Quando si apporta una modifica non autorizzata, la modifica viene contrassegnata con una sottolineatura ondulata di colore viola e nell'Elenco attività viene visualizzata un'attività. Per poter continuare a utilizzare Modifica e continuazione, è necessario annullare la modifica non autorizzata. Alcune modifiche non autorizzate sono consentite se effettuate all'esterno di Modifica e continuazione. Se si desidera mantenere i risultati di tale modifica non autorizzata, è necessario interrompere il debug e riavviare l'applicazione.

 Modifica e continuazione è supportata nelle applicazioni x86 e x64 destinate a .NET Framework 4.6 e App UWP per Windows 10 desktop o versioni successive (.NET Framework è solo una versione desktop).

 > [!NOTE]
 > Piattaforme e applicazioni non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

 Modifica e continuazione non è supportato quando si avvia il debug con il comando **Connetti a processo**. Modifica e continuazione non è supportato per codice ottimizzato o una combinazione di codice gestito e nativo. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Negli argomenti di questa sezione vengono fornite informazioni dettagliate sull'utilizzo di questa funzionalità e sui tipi di modifiche non consentiti.

## <a name="in-this-section"></a>In questa sezione
 [Procedura: Applicare modifiche in modalità interruzione con modifica e continuazione](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) viene illustrato come applicare modifiche al codice in modalità di interruzione.

 [Modifiche supportate al codice (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md) vengono descritti i tipi di modifiche. non possono essere eseguita nella [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] modifica e continuazione.

## <a name="related-sections"></a>Sezioni correlate
 [Modifica e continuazione](../debugger/edit-and-continue.md) fornisce un elenco di argomenti su Modifica e continuazione.
