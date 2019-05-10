---
title: Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3b577dc32a233d1f18518aa27001f340c634314c
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458176"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext

Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità che viene usata come tipo restituito per un <xref:System.Data.Linq.DataContext> metodo fa sì che la compilazione del progetto esito negativo. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.

Per ripristinare i tipi generati automaticamente originali dei tipi restituiti dei metodi <xref:System.Data.Linq.DataContext>, eliminare prima di tutto il metodo <xref:System.Data.Linq.DataContext> dal riquadro **Metodi** e quindi trascinare nuovamente l'oggetto da **Esplora server**/**Esplora database** in **Object Relational Designer**.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Identificare i metodi <xref:System.Data.Linq.DataContext> che usano la classe di entità come tipo restituito selezionando un metodo <xref:System.Data.Linq.DataContext> nel riquadro **Metodi** e controllando la proprietà **Return Type** nella finestra **Proprietà**.

2. Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)