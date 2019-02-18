---
title: 'Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e13de2f53622923aef1d4870de30be1afdf891ac
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942908"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)

È possibile aggiungere stored procedure e funzioni per i **O/R Designer** come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>. Per informazioni dettagliate sui <xref:System.Data.Linq.DataContext> metodi, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> È anche possibile usare le stored procedure per sostituire il valore predefinito [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento di runtime che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="create-datacontext-methods"></a>Creare metodi DataContext

È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando stored procedure o funzioni da <strong>Esplora Server o * * Database Explorer</strong> nel **O/R Designer**.

> [!NOTE]
> Il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> metodo varia a seconda di dove si rilascia la stored procedure o funzione nel **O/R Designer**. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, Eliminazione di elementi in un'area vuota del **O/R Designer** crea un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro **Metodi**. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente

1.  Nelle **Esplora Server** oppure **Esplora Database**, espandere il **Stored procedure** nodo del database con cui si lavora.

2.  Individuare la stored procedure desiderata e trascinarla in un'area vuota del **O/R Designer**.

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con un tipo restituito generato automaticamente e viene visualizzato nel riquadro **Metodi**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità

1.  Nelle **Esplora Server** oppure **Esplora Database**, espandere il **Stored procedure** nodo del database con cui si lavora.

2.  Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente nel **O/R Designer**.

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel riquadro **Metodi**.

> [!NOTE]
> Per informazioni su come modificare il tipo restituito predefinito esistente <xref:System.Data.Linq.DataContext> metodi, vedere [come: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)