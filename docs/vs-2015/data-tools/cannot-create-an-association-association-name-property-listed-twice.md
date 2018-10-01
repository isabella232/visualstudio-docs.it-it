---
title: Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: c6f410f798fff059220b544303d67990f46ca0ea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517996"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [non è possibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte](https://docs.microsoft.com/visualstudio/data-tools/cannot-create-an-association-association-name-property-listed-twice).  
  
  
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

