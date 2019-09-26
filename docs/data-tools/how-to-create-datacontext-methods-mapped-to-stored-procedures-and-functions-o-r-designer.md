---
title: Eseguire il mapping di metodi DataContext a sprocs e funzioni (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4c3769634bfbeb98fcc31e5c074177d950248292
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252900"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)

È possibile aggiungere le stored procedure e le funzioni alla finestra di progettazione di <xref:System.Data.Linq.DataContext> **O/R** come metodi. La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>. Per informazioni dettagliate sui <xref:System.Data.Linq.DataContext> metodi, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> È inoltre possibile utilizzare stored procedure per eseguire l'override [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] del comportamento di runtime predefinito che esegue inserimenti, aggiornamenti ed eliminazioni quando le modifiche vengono salvate dalle classi di entità in un database. Per altre informazioni, vedere [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Creazione di metodi DataContext

È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando le stored procedure o le funzioni da <strong>Esplora server o * * Esplora database</strong> su **Progettazione relazionale di o/R**.

> [!NOTE]
> Il tipo restituito del metodo generato <xref:System.Data.Linq.DataContext> varia a seconda della posizione in cui si rilascia la stored procedure o la funzione in **o/R Designer**. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, Se si eliminano elementi in un'area vuota di **Progettazione relazionale** oggetti <xref:System.Data.Linq.DataContext> , viene creato un metodo che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro **Metodi**. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente

1. In **Esplora server** o **Esplora database**espandere il nodo **stored procedure** del database con cui si sta lavorando.

2. Individuare la stored procedure desiderata e trascinarla in un'area vuota della **finestra di progettazione O/R**.

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con un tipo restituito generato automaticamente e viene visualizzato nel riquadro **Metodi**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità

1. In **Esplora server** o **Esplora database**espandere il nodo **stored procedure** del database con cui si sta lavorando.

2. Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente in **O/R Designer**.

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel riquadro **Metodi**.

> [!NOTE]
> Per informazioni sulla modifica del tipo restituito dei metodi <xref:System.Data.Linq.DataContext> esistenti, vedere [procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura dettagliata: Creazione di classi di LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)
