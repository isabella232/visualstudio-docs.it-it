---
title: 'Procedura: usare modifica e continuazione (c#) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d4305c39c62dfcc927ea7295ceec786d3da40f56
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527300"
---
# <a name="how-to-use-edit-and-continue-c"></a>Procedura: utilizzare Modifica e continuazione (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: usare modifica e continuazione (c#)](https://docs.microsoft.com/visualstudio/debugger/how-to-use-edit-and-continue-csharp).  
  
La funzionalità Modifica e continuazione per C# consente di apportare modifiche al codice in modalità di interruzione durante il debug. Le modifiche possono essere applicate senza terminare e riavviare la sessione di debug.  
  
 Modifica e continuazione viene richiamata automaticamente quando si apportano modifiche in modalità di interruzione, quindi sceglie una debugger l'esecuzione del comando, ad esempio **continuazione**, **passaggio**, o **Imposta istruzione successiva**, oppure si valuta una funzione in una finestra del debugger.  
  
> [!NOTE]
>  La funzionalità Modifica e continuazione non è supportata quando si esegue il debug di Compact Framework, codice ottimizzato, codice misto nativo/gestito o codice di integrazione di CLR (Common Language Runtime) in SQL Server. Se si tenta di applicare modifiche al codice in uno di questi scenari, verrà visualizzata una finestra di dialogo che spiega che modifica e continuazione non è supportato.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Per richiamare modifica e continuazione automaticamente  
  
1.  In modalità di interruzione, apportare una modifica al codice sorgente.  
  
2.  Dal **eseguire il Debug** dal menu fare clic su **continua**, **passaggio**, oppure **Imposta istruzione successiva** o valuta una funzione in una finestra del debugger.  
  
     Il nuovo codice viene compilato e il debug continua con il nuovo codice. Alcune modifiche non sono supportate in modifica e continuazione. Per altre informazioni, vedere [modifiche al codice supportate (c#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nel **le opzioni** finestra di dialogo espandere il **debug** nodo e selezionare **modifica e continuazione**.  
  
3.  Nel **le opzioni** finestra di dialogo **modifica e continuazione** pagina, selezionare o deselezionare i **Abilita modifica e continuazione** casella di controllo.  
  
     L'impostazione diventa effettiva quando si riavvia la sessione di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione (Visual c#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Modifiche al codice supportate (c#)](../debugger/supported-code-changes-csharp.md)   
 [Errori e avvisi di Modifica e continuazione (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)



