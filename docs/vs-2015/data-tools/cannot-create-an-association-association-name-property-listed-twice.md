---
title: Impossibile creare un'associazione &lt;il nome dell'associazione&gt; -proprietà è elencata due volte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cc3ebfcd9ad335cf95894aa916412da1a91cf008
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966111"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. La stessa proprietà è elencata più volte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Impossibile creare un'associazione \<nome associazione>. La stessa proprietà è elencata più volte: \<nome proprietà>.  
  
 Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà possono essere elencate una sola volta per ogni classe nell'associazione.  
  
 La proprietà specificata nel messaggio viene visualizzata più volte nelle **Proprietà associazione** della classe padre o figlio.  
  
### <a name="to-resolve-this-condition"></a>Risoluzione del problema  
  
-   Esaminare il messaggio e prendere nota della proprietà specificata in esso.  
  
-   Fare clic su **OK** per chiudere la finestra del messaggio.  
  
-   Controllare le **Proprietà associazione** e rimuovere le voci duplicate.  
  
-   Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](http://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186)   
 [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
