---
title: 'Procedura: modificare il tipo restituito di un metodo DataContext (O-R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5c67d6dea4c64e858acdab25ecc4a6cede6bf262
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089357"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)
Il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo (creato in una stored procedure o funzione di base) è diverso a seconda di dove si rilascia la stored procedure o funzione nel **O/R Designer**. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se si rilascia un elemento in un'area vuota del **O/R Designer**, un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente è stato creato. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo, selezionarla e fare clic sul **Return Type** proprietà nel **proprietà** finestra.

> [!NOTE]
>  Non è possibile ripristinare <xref:System.Data.Linq.DataContext> metodi che hanno un tipo restituito impostato su una classe di entità per restituire il tipo generato automaticamente usando il **proprietà** finestra. Per ripristinare un <xref:System.Data.Linq.DataContext> per restituire un tipo generato automaticamente, è necessario trascinare l'oggetto di database originale nel **O/R Designer** nuovamente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità

1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.

2.  Selezionare **Return Type** nel **delle proprietà** classe finestra e quindi selezionare un'entità disponibile nel **Return Type** elenco. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla nel **O/R Designer** per aggiungerlo all'elenco.

3.  Salvare il *dbml* file.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente

1.  Selezionare il <xref:System.Data.Linq.DataContext> metodo nella **metodi** riquadro ed eliminarlo.

2.  Trascinare l'oggetto di database dalla **Esplora Server** oppure **Esplora Database** in un'area vuota del **O/R Designer**.

3.  Salvare il *dbml* file.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)