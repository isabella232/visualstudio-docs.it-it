---
title: La proprietà &lt;nome della proprietà&gt; non può essere eliminato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 98b065500c9c881a7190b59c4d70a0433eb8864c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186524"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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

