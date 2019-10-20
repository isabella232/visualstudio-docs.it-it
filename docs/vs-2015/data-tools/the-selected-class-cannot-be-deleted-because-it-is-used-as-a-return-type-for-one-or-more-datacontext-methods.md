---
title: Non è possibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667262"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità usata come tipo restituito di un metodo <xref:System.Data.Linq.DataContext> determinerà l'esito negativo della compilazione del progetto. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.

 Per ripristinare i tipi restituiti dei metodi di <xref:System.Data.Linq.DataContext> ai tipi generati automaticamente originali, eliminare prima il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi, quindi trascinare di nuovo l'oggetto da **Esplora server** /**Esplora database** in Progettazione relazionale oggetti.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Identificare <xref:System.Data.Linq.DataContext> metodi che usano la classe di entità come tipo restituito selezionando un metodo di <xref:System.Data.Linq.DataContext> nel riquadro dei metodi ed esaminando la proprietà del **tipo restituito** nella finestra **Proprietà** .

2. Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura: modificare il tipo restituito di un metodo DataContext (o/r designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
