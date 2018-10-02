---
title: La proprietà &lt;nome della proprietà&gt; non può essere eliminato | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 22884e69c4802ec0bf699e383f0339d840f515e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518840"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [la proprietà &lt;NomeProprietà&gt; non può essere eliminato](https://docs.microsoft.com/visualstudio/data-tools/the-property-property-name-cannot-be-deleted).  
  
  
La proprietà \<nome proprietà > non può essere eliminato perché è impostato come proprietà Discriminator per l'ereditarietà tra \<nome classe > e \<nome classe >  
  
 La proprietà selezionata viene impostata come la **Discriminator Property** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.  
  
 Impostare il **Discriminator Property** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Impostare il **discriminatore** proprietà su una diversa proprietà.  
  
3.  Provare a eliminare nuovamente la proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)   
 [Ereditarietà della classe di dati (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)

