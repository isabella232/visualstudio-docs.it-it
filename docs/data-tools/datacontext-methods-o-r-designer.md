---
title: Metodi DataContext (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 83ca0059e576683571435764914bf0087eded2fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951163"
---
# <a name="datacontext-methods-or-designer"></a>Metodi DataContext (O/R Designer)

<xref:System.Data.Linq.DataContext> metodi (nel contesto del [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sono metodi del <xref:System.Data.Linq.DataContext> classi che eseguono stored procedure e funzioni in un database.

La classe <xref:System.Data.Linq.DataContext> rappresenta una classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] che funge da canale tra un database SQL Server e le classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tale database. La classe <xref:System.Data.Linq.DataContext> contiene le informazioni sulla stringa di connessione e i metodi per la connessione a un database e la modifica dei dati presenti in esso. Per impostazione predefinita, la classe <xref:System.Data.Linq.DataContext> contiene diversi metodi che è possibile chiamare, ad esempio il metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A> che invia dati aggiornati dalle classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] al database. È anche possibile creare metodi <xref:System.Data.Linq.DataContext> aggiuntivi mappati a stored procedure e funzioni. In altre parole, vengono chiamati questi metodi personalizzati viene eseguita la stored procedure o funzione nel database a cui il <xref:System.Data.Linq.DataContext> metodo viene eseguito il mapping. È possibile aggiungere nuovi metodi alla classe <xref:System.Data.Linq.DataContext> nello stesso modo in cui si aggiungono per estendere qualsiasi classe. Tuttavia, nelle discussioni sulle <xref:System.Data.Linq.DataContext> metodi nel contesto del **O/R Designer**, è il <xref:System.Data.Linq.DataContext> metodi che eseguono il mapping a stored procedure e funzioni che vengono discussi.

## <a name="methods-pane"></a>Riquadro Metodi

<xref:System.Data.Linq.DataContext> i metodi che eseguono il mapping a stored procedure e funzioni sono visualizzati nel **metodi** riquadro della finestra il **O/R Designer**. Il riquadro **Metodi** rappresenta il riquadro situato a lato del riquadro **Entità** (l'area di progettazione principale). Il **metodi** riquadro sono elencate tutte <xref:System.Data.Linq.DataContext> metodi creato utilizzando la **O/R Designer**. Per impostazione predefinita, il **metodi** riquadro è vuoto; trascinare stored procedure o funzioni da **Esplora Server** oppure **Esplora Database** nel **O/R Designer**  per creare <xref:System.Data.Linq.DataContext> metodi e popolare le **metodi** riquadro. Per altre informazioni, vedere [procedura: metodi creare DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Aprire e chiudere il riquadro dei metodi facendo clic con il **O/R Designer** e quindi scegliendo **Nascondi riquadro metodi** oppure **Mostra riquadro metodi**, oppure usare il tasto di scelta rapida  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Due tipi di metodi DataContext

I metodi DataContext sono metodi con mapping a stored procedure e funzioni nel database. È possibile creare e aggiungere metodi DataContext nel **metodi** riquadro della finestra di **O/R Designer**. Esistono due tipi distinti di metodi <xref:System.Data.Linq.DataContext>: quelli che restituiscono uno o più set di risultati e quelli che non restituiscono alcun set di risultati:

- Metodi <xref:System.Data.Linq.DataContext> che restituiscono uno o più set di risultati:

   Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure e funzioni nel database e restituire i risultati. Per altre informazioni, vedere [procedura: metodi creare DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, e <xref:System.Data.Linq.IMultipleResults>.

- Metodi <xref:System.Data.Linq.DataContext> che non restituiscono set di risultati, ad esempio inserimenti, aggiornamenti ed eliminazioni per una classe di entità specifica.

   Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure invece di usare il comportamento [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito per salvare i dati modificati tra una classe di entità e il database. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Tipi restituiti dei metodi DataContext

Quando si trascinano stored procedure e funzioni dal **Esplora Server** oppure **Esplora Database** nel **O/R Designer**, il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> metodo varia a seconda di dove si rilascia l'elemento. Eliminazione degli elementi direttamente in una classe di entità esistente crea un <xref:System.Data.Linq.DataContext> metodo con il tipo restituito della classe di entità; rilascio degli elementi in un'area vuota del **O/R Designer** (in dei riquadri) crea un <xref:System.Data.Linq.DataContext> (metodo) che restituisce un tipo generato automaticamente. Il tipo generato automaticamente con il nome che corrisponde a stored procedure o nome della funzione e le proprietà, eseguire il mapping ai campi restituiti dalla stored procedure o funzione.

> [!NOTE]
> È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Gli oggetti trascinati dal database nell'area di Progettazione relazionale oggetti vengono denominati automaticamente, in base al nome degli oggetti nel database. Se si trascina più volte lo stesso oggetto, viene aggiunto un numero alla fine del nuovo nome che distingue i nomi. Se i nomi degli oggetti di database contengono spazi o caratteri non supportati in Visual Basic o C#, lo spazio o il carattere non valido viene sostituito con un carattere di sottolineatura.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Stored procedure](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)