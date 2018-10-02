---
title: La proprietà &lt;nome della proprietà&gt; non può essere eliminato perché è inclusa nell'associazione &lt;il nome dell'associazione&gt; | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6983d52615219c386b049eea33f9f911956c6d59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525806"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato perché è inclusa nell'associazione &lt;nome associazione&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la proprietà &lt;NomeProprietà&gt; non può essere eliminato perché è inclusa nell'associazione &lt;il nome dell'associazione&gt;](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name).  
  
  
La proprietà selezionata viene impostata come la **proprietà di associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.  
  
 Impostare il **proprietà di associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Selezionare la linea di associazione in Progettazione relazionale oggetti che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Fare doppio clic sulla linea per aprire la **Editor di associazione** nella finestra di dialogo.  
  
3.  Rimuovere la proprietà di **le proprietà di associazione**.  
  
4.  Provare a eliminare nuovamente la proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

