---
title: Finestra di dialogo Editor raccolta di tipi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: c33049c264041495041798ab98c4223ebe0ed6f7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298571"
---
# <a name="type-collection-editor-dialog-box"></a>Finestra di dialogo Editor raccolta di tipi
Il **Editor raccolta di tipi** finestra di dialogo consente di aggiungere tipi noti per il **inviare** e **ricezione** attività. Questa finestra di dialogo viene usato anche per aggiungere argomenti tipo generico per il **InvokeMethod** attività. Quando viene utilizzato per il **inviare** e **ricezione** attività per aggiungere tipi noti, il **Editor raccolta di tipi** nella finestra di dialogo richiede tali aggiunte siano univoche. Se viene aggiunto un tipo duplicato e viene eseguito il commit della modifica facendo **OK**, viene restituito un messaggio di errore. Quando viene utilizzato per il **InvokeMethod** attività per aggiungere argomenti tipo generico, il **Editor raccolta di tipi** nella finestra di dialogo consente l'aggiunta di tipi duplicati.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../includes/crabout-md.md)] i tipi noti, vedere [Data Contract Known Types](http://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).  
  
 La tabella seguente descrive gli elementi dell'interfaccia utente di **raccolta di tipi** nella finestra di dialogo.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|----------------|-----------------|  
|**Elenco dei tipi**|Un elenco dei tipi che sono stati aggiunti o rimossi.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>Per visualizzare Editor raccolta di tipi  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Per visualizzare Editor raccolta di tipi per le attività Send e Receive  
  
1.  Selezionare il **inviare** oppure **ricezione** attività nella visualizzazione progettazione.  
  
2.  Premere **F4** per visualizzare i **proprietà** finestra.  
  
3.  Nel **delle proprietà** finestra, fare clic sul pulsante dei puntini di sospensione accanto alle **KnownTypes** proprietà.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Per visualizzare Editor raccolta di tipi per l'attività InvokeMethod  
  
1.  Selezionare il **InvokeMethod** attività nella visualizzazione progettazione.  
  
2.  Premere **F4** per visualizzare i **proprietà** finestra.  
  
3.  Nel **delle proprietà** finestra, fare clic sul pulsante dei puntini di sospensione accanto alle **GenericTypeArguments** proprietà.