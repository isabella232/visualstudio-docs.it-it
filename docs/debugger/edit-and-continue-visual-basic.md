---
title: Modifica e continuazione (Visual Basic) | Microsoft Docs
description: La funzionalità modifica e continuazione è disponibile per i progetti Visual Basic. Informazioni sulle modifiche supportate e su come è possibile controllare se e quando vengono applicate le modifiche.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f5df9910d779a4c360a0c1f3b6482b5c51256d29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871923"
---
# <a name="edit-and-continue-visual-basic"></a>Modifica e continuazione (Visual Basic)
Modifica e continuazione è una funzionalità per il debug di [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] che consente di apportare modifiche al codice mentre viene eseguito in modalità di interruzione. Dopo aver applicato le modifiche al codice, è possibile riprendere l'esecuzione del codice con le nuove modifiche già inserite e verificarne l'effetto.

 La funzionalità Modifica e continuazione può essere utilizzata ogni volta che si attiva la modalità di interruzione. In modalità di rottura, il puntatore all'istruzione, una freccia gialla nella finestra di origine, punta alla riga che contiene un'istruzione eseguibile in un corpo del metodo o della proprietà che verrà eseguito successivamente.

 La modalità Modifica e continuazione supporta la maggior parte delle modifiche che è necessario apportare durante una sessione di debug, con alcune eccezioni. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Quando si apporta una modifica non autorizzata, la modifica viene contrassegnata con una sottolineatura ondulata di colore viola e nell'Elenco attività viene visualizzata un'attività. Per poter continuare a utilizzare Modifica e continuazione, è necessario annullare la modifica non autorizzata. Alcune modifiche non autorizzate sono consentite se effettuate all'esterno di Modifica e continuazione. Se si desidera mantenere i risultati di tale modifica non autorizzata, è necessario interrompere il debug e riavviare l'applicazione.

 La funzionalità modifica e continuazione è supportata nelle app UWP per Windows 10 e nelle app x86 e x64 destinate a .NET Framework 4,6 desktop o versioni successive (il .NET Framework è solo una versione desktop).

 > [!NOTE]
 > Le app e le piattaforme non supportate includono ASP.NET 5, Silverlight 5 e Windows 8.1.

 Modifica e continuazione non è supportato quando si avvia il debug con il comando **Connetti a processo**. La funzionalità modifica e continuazione non è supportata per codice ottimizzato o codice nativo e gestito misto. Per altre informazioni, vedere [modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Negli argomenti di questa sezione vengono fornite informazioni dettagliate sull'utilizzo di questa funzionalità e sui tipi di modifiche non consentiti.

## <a name="in-this-section"></a>Contenuto della sezione
 [Procedura: applicare modifiche in modalità di interruzioni con modifica e continuazione](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Viene illustrato come applicare modifiche al codice in modalità di interruzioni.

 [Modifiche al codice supportate (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md) Descrive i tipi di modifiche che non possono essere eseguite in [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] modifica e continuazione.

## <a name="related-sections"></a>Sezioni correlate
 [Modifica e continuazione](../debugger/edit-and-continue.md) Viene fornito un elenco di argomenti relativi a modifica e continuazione.
