---
title: Eseguire il mapping di metodi DataContext a sprocs e funzioni (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fa392467024a38dc447e6a5077f855d3464103b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648361"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)

È possibile aggiungere le stored procedure e le funzioni alla **finestra di progettazione di O/R** come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>. Per informazioni dettagliate sui metodi di <xref:System.Data.Linq.DataContext>, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> È inoltre possibile utilizzare stored procedure per sostituire il comportamento predefinito del [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] Runtime che esegue inserimenti, aggiornamenti ed eliminazioni quando le modifiche vengono salvate dalle classi di entità in un database. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Creazione di metodi DataContext

È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando le stored procedure o le funzioni da <strong>Esplora server o * * Esplora database</strong> in **Progettazione relazionale**o.

> [!NOTE]
> Il tipo restituito del metodo di <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia la funzione o stored procedure in **Progettazione relazionale**o. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, Se si eliminano elementi in un'area vuota di **Progettazione relazionale** oggetti, viene creato un metodo di <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro **Metodi**. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

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
> Per informazioni su come modificare il tipo restituito predefinito esistente <xref:System.Data.Linq.DataContext> metodi, vedere [come: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura dettagliata: creazione di classi di LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)
