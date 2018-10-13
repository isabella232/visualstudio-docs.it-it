---
title: Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ae0458a0921177bfe3a5a8b499131c6dd5c3de5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172068"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Impossibile creare un'associazione \<nome associazione >. La stessa proprietà è elencata più volte: \<nome proprietà >.  
  
 Le associazioni vengono definite dall'oggetto selezionato **le proprietà di associazione** nel **Editor di associazione** nella finestra di dialogo. Le proprietà possono essere elencate una sola volta per ogni classe nell'associazione.  
  
 La proprietà nel messaggio viene visualizzato più di una volta nell'elemento padre o figlio della classe **le proprietà di associazione**.  
  
### <a name="to-resolve-this-condition"></a>Risoluzione del problema  
  
-   Esaminare il messaggio e prendere nota della proprietà specificata in esso.  
  
-   Fare clic su **OK** per chiudere la finestra di messaggio.  
  
-   Esaminare i **le proprietà di associazione** e rimuovere le voci duplicate.  
  
-   Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](http://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

