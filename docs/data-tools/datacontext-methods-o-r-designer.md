---
title: Metodi DataContext (Object Relational Designer)
description: Comprendere i metodi DataContext nel contesto degli strumenti LINQ to SQL per Visual Studio. Questi metodi eseguono stored procedure e funzioni in un database.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 892005ee4f88b1ffc4cd456a2e4ccbfe3e0ee50b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037005"
---
# <a name="datacontext-methods-or-designer"></a>Metodi DataContext (O/R Designer)

<xref:System.Data.Linq.DataContext>I metodi (nel contesto degli strumenti [LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sono metodi della classe che eseguono stored procedure e funzioni in un <xref:System.Data.Linq.DataContext> database.

La classe <xref:System.Data.Linq.DataContext> rappresenta una classe [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] che funge da canale tra un database SQL Server e le classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tale database. La classe <xref:System.Data.Linq.DataContext> contiene le informazioni sulla stringa di connessione e i metodi per la connessione a un database e la modifica dei dati presenti in esso. Per impostazione predefinita, la classe <xref:System.Data.Linq.DataContext> contiene diversi metodi che è possibile chiamare, ad esempio il metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A> che invia dati aggiornati dalle classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] al database. È anche possibile creare metodi <xref:System.Data.Linq.DataContext> aggiuntivi mappati a stored procedure e funzioni. In altre parole, la chiamata di questi metodi personalizzati esegue stored procedure funzione o nel database a cui è <xref:System.Data.Linq.DataContext> mappato il metodo. È possibile aggiungere nuovi metodi alla classe <xref:System.Data.Linq.DataContext> nello stesso modo in cui si aggiungono per estendere qualsiasi classe. Tuttavia, nelle discussioni sui metodi nel contesto di <xref:System.Data.Linq.DataContext> **O/R Designer**, si tratta dei metodi che eseere ese ne viene illustrato il mapping a stored procedure <xref:System.Data.Linq.DataContext> e funzioni.

## <a name="methods-pane"></a>Riquadro Metodi

<xref:System.Data.Linq.DataContext>I metodi mappati a stored procedure e funzioni vengono visualizzati nel **riquadro** Metodi di **O/R Designer.** Il riquadro **Metodi** rappresenta il riquadro situato a lato del riquadro **Entità** (l'area di progettazione principale). Nel **riquadro** Metodi sono <xref:System.Data.Linq.DataContext> elencati tutti i metodi creati tramite **O/R Designer.** Per impostazione predefinita, **il riquadro** Metodi è vuoto. Trascinare stored procedure o funzioni **Esplora server** o **Esplora database** in **Progettazione** oggetti per creare metodi e popolare <xref:System.Data.Linq.DataContext> il **riquadro** Metodi. Per altre informazioni, vedere Procedura: Creare metodi DataContext mappati a stored procedure e funzioni [(O/R Designer).](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

> [!NOTE]
> Aprire e chiudere il riquadro dei metodi facendo clic  con il pulsante destro del mouse su **O/R Designer** e quindi scegliendo Nascondi riquadro metodi o Mostra riquadro **metodi** oppure usare i tasti di scelta **rapida CTRL** + **1.**

## <a name="two-types-of-datacontext-methods"></a>Due tipi di metodi DataContext

I metodi DataContext sono metodi con mapping a stored procedure e funzioni nel database. È possibile creare e aggiungere metodi DataContext nel **riquadro Metodi** di **O/R Designer.** Esistono due tipi distinti di metodi <xref:System.Data.Linq.DataContext>: quelli che restituiscono uno o più set di risultati e quelli che non restituiscono alcun set di risultati:

- Metodi <xref:System.Data.Linq.DataContext> che restituiscono uno o più set di risultati:

   Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure e funzioni nel database e restituire i risultati. Per altre informazioni, vedere Procedura: Creare metodi DataContext mappati a stored procedure e funzioni [(O/R Designer),](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)System.Data.Linq.ISingleResult \<T> e <xref:System.Data.Linq.IMultipleResults> .

- Metodi <xref:System.Data.Linq.DataContext> che non restituiscono set di risultati, ad esempio inserimenti, aggiornamenti ed eliminazioni per una classe di entità specifica.

   Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure invece di usare il comportamento [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito per salvare i dati modificati tra una classe di entità e il database. Per altre informazioni, vedere Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni [(O/R Designer).](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)

## <a name="return-types-of-datacontext-methods"></a>Tipi restituiti dei metodi DataContext

Quando si trascinano stored procedure e funzioni da Esplora server o **Esplora database in** **O/R Designer,** il tipo restituito del metodo generato varia **a** seconda della posizione in cui si rilascia <xref:System.Data.Linq.DataContext> l'elemento. L'eliminazione diretta degli elementi in una classe di entità esistente crea un metodo con il tipo restituito della classe di entità. L'eliminazione di elementi in un'area vuota di Progettazione oggetti (in entrambi i riquadri) crea un metodo che restituisce un tipo generato <xref:System.Data.Linq.DataContext>  <xref:System.Data.Linq.DataContext> automaticamente. Il tipo generato automaticamente ha il nome corrispondente al nome stored procedure o alla funzione e alle proprietà, che vengono mappati ai campi restituiti dal stored procedure o dalla funzione.

> [!NOTE]
> È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, [vedere Procedura: Modificare il tipo restituito di un metodo DataContext (O/R Designer).](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

Gli oggetti trascinati dal database nell'area di Progettazione relazionale oggetti vengono denominati automaticamente in base al nome degli oggetti nel database. Se si trascina lo stesso oggetto più volte, viene aggiunto un numero alla fine del nuovo nome che differenzia i nomi. Se i nomi degli oggetti di database contengono spazi o caratteri non supportati in Visual Basic o C#, lo spazio o il carattere non valido viene sostituito con un carattere di sottolineatura.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Stored procedure](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
