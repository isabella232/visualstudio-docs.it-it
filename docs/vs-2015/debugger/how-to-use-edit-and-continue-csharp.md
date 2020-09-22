---
title: 'Procedura: usare modifica e continuazione (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839736"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: utilizzare Modifica e continuazione (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La funzionalità Modifica e continuazione per C# consente di apportare modifiche al codice in modalità di interruzione durante il debug. Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug.  
  
 La funzionalità modifica e continuazione viene richiamata automaticamente quando si apportano modifiche in modalità di interruzione, quindi si sceglie un comando di esecuzione del debugger, ad esempio **continua**, **Esegui** **istruzione o imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.  
  
> [!NOTE]
> La funzionalità Modifica e continuazione non è supportata quando si esegue il debug di Compact Framework, codice ottimizzato, codice misto nativo/gestito o codice di integrazione di CLR (Common Language Runtime) in SQL Server. Se si tenta di applicare modifiche al codice in uno di questi scenari, viene visualizzata una finestra di dialogo in cui viene spiegato che la funzionalità modifica e continuazione non è supportata.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Per richiamare automaticamente modifica e continuazione  
  
1. In modalità di rottura apportare una modifica al codice sorgente.  
  
2. Dal menu **debug** , fare clic su **continua**, **Esegui** **istruzione o imposta istruzione successiva** o valuta una funzione in una finestra del debugger.  
  
     Il nuovo codice viene compilato e il debug continua con il nuovo codice. Alcune modifiche non sono supportate da modifica e continuazione. Per altre informazioni, vedere [modifiche al codice supportate (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1. Scegliere **Opzioni** dal menu **Strumenti**.  
  
2. Nella finestra di dialogo **Opzioni** espandere il nodo **debug** e selezionare **modifica e continua**.  
  
3. Nella pagina **Opzioni** della finestra di dialogo **modifica e continuazione** Selezionare o deselezionare la casella di controllo **Abilita modifica e continuazione** .  
  
     L'impostazione viene applicata quando si riavvia la sessione di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifiche al codice supportate (C#)](../debugger/supported-code-changes-csharp.md)   
 [Errori e avvisi di modifica e continuazione (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
