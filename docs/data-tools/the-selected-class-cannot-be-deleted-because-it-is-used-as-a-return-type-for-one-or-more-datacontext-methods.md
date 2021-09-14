---
title: Impossibile eliminare la classe selezionata
description: Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1099369fdf2ebe4ef2ba4cfc8b8d6fabf7e47323
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631133"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext

Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità usata come tipo restituito per un metodo causa <xref:System.Data.Linq.DataContext> l'esito negativo della compilazione del progetto. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.

Per ripristinare i tipi generati automaticamente originali dei tipi restituiti dei metodi <xref:System.Data.Linq.DataContext>, eliminare prima di tutto il metodo <xref:System.Data.Linq.DataContext> dal riquadro **Metodi** e quindi trascinare nuovamente l'oggetto da **Esplora server**/**Esplora database** in **Object Relational Designer**.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Identificare i metodi <xref:System.Data.Linq.DataContext> che usano la classe di entità come tipo restituito selezionando un metodo <xref:System.Data.Linq.DataContext> nel riquadro **Metodi** e controllando la proprietà **Return Type** nella finestra **Proprietà**.

2. Impostare **Return Type** su una classe di entità diversa oppure eliminare il metodo <xref:System.Data.Linq.DataContext> dal riquadro dei metodi.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
