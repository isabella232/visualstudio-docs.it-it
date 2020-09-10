---
title: Non è possibile eliminare la classe selezionata
description: Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 84fabc7f0f1efdf06006597aec9bb813578589a8
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743257"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext

Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità utilizzata come tipo restituito per un <xref:System.Data.Linq.DataContext> metodo comporta l'esito negativo della compilazione del progetto. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.

Per ripristinare i tipi generati automaticamente originali dei tipi restituiti dei metodi <xref:System.Data.Linq.DataContext>, eliminare prima di tutto il metodo <xref:System.Data.Linq.DataContext> dal riquadro **Metodi** e quindi trascinare nuovamente l'oggetto da **Esplora server**/**Esplora database** in **Object Relational Designer**.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Identificare i metodi <xref:System.Data.Linq.DataContext> che usano la classe di entità come tipo restituito selezionando un metodo <xref:System.Data.Linq.DataContext> nel riquadro **Metodi** e controllando la proprietà **Return Type** nella finestra **Proprietà**.

2. Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.

## <a name="see-also"></a>Vedere anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
