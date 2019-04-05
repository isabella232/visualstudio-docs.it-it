---
title: La classe selezionata non può essere eliminata perché è usato come tipo restituito per uno o più metodi DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ad1ccf45a2df6a0b1b23208926136aa2b09eabd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964791"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità usata come tipo restituito di un metodo <xref:System.Data.Linq.DataContext> determinerà l'esito negativo della compilazione del progetto. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.  
  
 Per ripristinare i tipi restituiti dei <xref:System.Data.Linq.DataContext> metodi nei tipi generati automaticamente originali, eliminare prima il <xref:System.Data.Linq.DataContext> metodo dal riquadro dei metodi e quindi trascinare l'oggetto dalla **Esplora Server** / **Database Explorer** in nuovamente la finestra di Progettazione relazionale oggetti.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Identificare <xref:System.Data.Linq.DataContext> metodi che usano la classe di entità come tipo restituito selezionando un <xref:System.Data.Linq.DataContext> metodo nei metodi riquadro ed esaminando il **Return Type** proprietà nel **proprietà** finestra .  
  
2.  Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
