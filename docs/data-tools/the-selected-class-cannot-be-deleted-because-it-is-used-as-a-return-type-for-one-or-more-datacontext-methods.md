---
title: Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 21ef0f86d701c899328044a03cde8035a1e7292d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174211"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Impossibile eliminare la classe selezionata perché è utilizzata come tipo restituito per uno o più metodi DataContext

Il tipo restituito di uno o più metodi <xref:System.Data.Linq.DataContext> rappresenta la classe di entità selezionata. L'eliminazione di una classe di entità che viene usata come tipo restituito per un <xref:System.Data.Linq.DataContext> metodo fa sì che la compilazione del progetto esito negativo. Per eliminare la classe di entità selezionata, identificare i metodi <xref:System.Data.Linq.DataContext> che l'usano e impostare i relativi tipi restituiti su una classe di entità diversa.

Per ripristinare i tipi restituiti dei <xref:System.Data.Linq.DataContext> metodi nei tipi generati automaticamente originali, eliminare prima il <xref:System.Data.Linq.DataContext> metodo dal **metodi** riquadro e quindi trascinare l'oggetto dalla **Esplora Server** / **Database Explorer** nel **O/R Designer** nuovamente.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Identificare <xref:System.Data.Linq.DataContext> metodi che usano la classe di entità come tipo restituito selezionando un <xref:System.Data.Linq.DataContext> metodo nella **metodi** riquadro ed esaminando il **Return Type** proprietà nella finestra di **Proprietà** finestra.

2. Impostare il **Return Type** a una classe di entità diverso o eliminare il <xref:System.Data.Linq.DataContext> metodo dal riquadro dei metodi.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)