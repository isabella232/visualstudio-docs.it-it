---
title: Eseguire il mapping di metodi DataContext a sproc e funzioni
description: Informazioni su come creare metodi DataContext di cui è stato eseguito il mapping a stored procedure (sproc) e funzioni usando Object Relational Designer (Progettazione O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 366d13085c14eebda3e9ca257d726d59167852b6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631314"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)

È possibile aggiungere stored procedure e funzioni a **O/R Designer** come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e il passaggio dei parametri obbligatori comportano l'esecuzione della stored procedure o funzione nel database e la restituzione dei dati nel tipo restituito del metodo <xref:System.Data.Linq.DataContext>. Per informazioni dettagliate sui <xref:System.Data.Linq.DataContext> metodi, vedere [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> È anche possibile usare le stored procedure per eseguire l'override del comportamento di run-time predefinito che esegue inserimenti, aggiornamenti ed eliminazioni quando le modifiche vengono salvate dalle classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un database. Per altre informazioni, vedere Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed [eliminazioni (O/R Designer).](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)

## <a name="create-datacontext-methods"></a>Creare metodi DataContext

È possibile creare metodi trascinando stored procedure o funzioni da Esplora server <xref:System.Data.Linq.DataContext> <strong>o **Esplora database</strong> in **O/R Designer.**

> [!NOTE]
> Il tipo restituito del metodo generato varia a seconda della posizione stored procedure o della funzione <xref:System.Data.Linq.DataContext> in **Progettazione O/R.** Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, L'eliminazione di elementi in un'area vuota di **O/R Designer** crea un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro **Metodi**. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [Procedura: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente

1. In **Esplora server** o **Esplora database** espandere il nodo **Stored procedure** del database con cui si sta lavorando.

2. Individuare il stored procedure desiderato e trascinarlo in un'area vuota di **O/R Designer.**

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con un tipo restituito generato automaticamente e viene visualizzato nel riquadro **Metodi**.

### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità

1. In **Esplora server** o **Esplora database** espandere il nodo **Stored procedure** del database con cui si sta lavorando.

2. Individuare il stored procedure desiderato e trascinarlo in una classe di entità esistente in **O/R Designer.**

     Il metodo <xref:System.Data.Linq.DataContext> viene creato con il tipo restituito della classe di entità selezionata e viene visualizzato nel riquadro **Metodi**.

> [!NOTE]
> Per informazioni su come modificare il tipo restituito predefinito esistente <xref:System.Data.Linq.DataContext> metodi, vedere [come: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Metodi DataContext (Progettazione O/R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura dettagliata: Creazione di LINQ to SQL personalizzate](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introduzione a LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ in C#](/dotnet/csharp/linq/linq-in-csharp)
