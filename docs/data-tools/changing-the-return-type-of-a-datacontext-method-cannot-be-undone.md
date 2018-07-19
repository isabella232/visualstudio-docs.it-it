---
title: La modifica del tipo restituito di un metodo DataContext non può essere annullata
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: abec4dd6d5cded79e1f25a6dbb5ec2e55c2d444f
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282755"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>La modifica del tipo restituito di un metodo DataContext non può essere annullata

La modifica del tipo restituito di un metodo DataContext non può essere annullata. Per ripristinare il tipo generato automaticamente, è necessario trascinare l'elemento dal **Esplora Server** oppure **Esplora Database** in nuovamente la finestra di Progettazione relazionale oggetti. Modificare il tipo restituito?

Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> varia a seconda della posizione in cui si rilascia l'elemento in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità. Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo, selezionarla e fare clic sul **Return Type** proprietà nel **proprietà** finestra.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Per modificare il tipo restituito di un metodo DataContext

- Scegliere **Sì**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Per uscire dalla finestra di messaggio e lasciare invariato il tipo restituito

- Fare clic su **No**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Per ripristinare il tipo restituito originale dopo la modifica del tipo restituito

1. Selezionare il <xref:System.Data.Linq.DataContext> metodo su di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] ed eliminarlo.

2. Individuare l'elemento in **Esplora Server/Esplora Database** e trascinarla nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito predefinito originale.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)