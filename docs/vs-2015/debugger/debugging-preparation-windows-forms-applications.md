---
title: 'Preparazione al debug: Applicazioni Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4997aa5f184fb5d6f0e9a3ccd08a9d829c26a0cc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765634"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Preparazione al debug: applicazioni Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il modello di progetto Windows Forms consente di creare un'applicazione Windows Forms. Il debug di questo tipo di applicazione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] è una procedura molto semplice. Per altre informazioni, vedere [creazione di un progetto di applicazione Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Quando si crea un progetto di Windows Form mediante il modello di progetto, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vengono definite automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio. Se necessario, è possibile modificare tali impostazioni. Queste impostazioni possono essere modificate nel  **\<nome progetto > pagine delle proprietà** nella finestra di dialogo (**progetto personale** in Visual Basic).  
  
 Per altre informazioni, vedere [impostazioni di proprietà consigliate](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Nella tabella riportata di seguito è indicata un'impostazione consigliata aggiuntiva per le proprietà.  
  
### <a name="configuration-properties-in-debug-tab"></a>Proprietà di configurazione disponibili nella scheda Debug  
  
|**Nome della proprietà**|**Impostazione**|  
|-----------------------|-----------------|  
|**Azione di avvio**|-Impostare su **progetto di avvio,** la maggior parte dei casi. Impostare su **Avvia programma esterno** se si desidera avviare un altro eseguibile quando si avvia il debug (in genere per il debug di DLL).|  
  
 È possibile eseguire il debug di applicazioni Windows Forms dall'interno di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oppure stabilendo una connessione a un'applicazione già in esecuzione. Per altre informazioni sul collegamento, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Per eseguire il debug di Windows Forms Application in C#, F# o Visual Basic  
  
1. Aprire il progetto in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2. Creare i punti di interruzione necessari.  
  
    Poiché le applicazioni Windows Forms sono guidate da eventi, i punti di interruzione dovranno essere inseriti nel codice del gestore eventi o nei metodi chiamati dal codice del gestore eventi. Alcuni eventi tipici in cui impostare i punti di interruzione sono:  
  
   1. Eventi associati a un controllo, ad esempio Click, Enter e così via  
  
   2. Eventi associati all'avvio e alla chiusura dell'applicazione, ad esempio Load, Activated e così via  
  
   3. Eventi di convalida e relativi allo stato attivo.  
  
      Per altre informazioni, vedere [Creazione di gestori eventi in Windows Forms](http://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. Nel **Debug** menu, fare clic su **avviare**.  
  
4. Eseguire il debug usando le tecniche descritte in [nozioni fondamentali di debug](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Procedura: Set di configurazioni di Debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Collegamento a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Form](http://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)



