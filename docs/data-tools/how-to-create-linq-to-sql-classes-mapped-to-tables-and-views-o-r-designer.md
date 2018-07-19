---
title: 'Procedura: creare LINQ to SQL classi mappate a tabelle e visualizzazioni (O-R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089325"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: creare LINQ to SQL classi mappate a tabelle e visualizzazioni (O/R Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] le classi che vengono eseguito il mapping alle tabelle di database e le viste vengono definite *le classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità che si basano su viste o tabelle di database trascinando le tabelle o viste dal **Esplora Server** oppure **Esplora Database** nel [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Il **O/R Designer** genera le classi e applica le specifiche [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gli attributi per abilitare [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funzionalità (la comunicazione dei dati e le funzionalità di modifica il <xref:System.Data.Linq.DataContext>). Per informazioni dettagliate sui [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] le classi, vedere [LINQ al modello a oggetti SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  Il **O/R Designer** è un mapper relazionale a oggetti semplice, perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creare LINQ alle classi di SQL che vengono eseguito il mapping alle tabelle di database o alle viste
 Trascinamento di tabelle o viste dal **Esplora Server** o **Esplora Database** nel **O/R Designer** consente di creare classi di entità oltre al <xref:System.Data.Linq.DataContext> metodi che vengono usati per eseguire gli aggiornamenti.

 Per impostazione predefinita, il runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se non si desidera questo comportamento, è possibile configurare una classe di entità per l'utilizzo di stored procedure per eseguire inserimenti, aggiornamenti ed eliminazioni invece di usare il valore predefinito [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento di runtime. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

1.  Nella **Server** o **Esplora Database**, espandere **tabelle** o **viste** e individuare la tabella di database o visualizzare che si desidera utilizzare di applicazione.

2.  Trascinare la tabella o la visualizzazione nel **O/R Designer**.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creare un'origine dati oggetto e visualizzare i dati in un form
 Dopo aver creato le classi di entità usando il **O/R Designer**, è possibile creare un'origine dati oggetto e popolare le [finestra Origini dati](add-new-data-sources.md) con le classi di entità.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL

1.  Nel **compilare** menu, fare clic su **Compila soluzione** per compilare il progetto.

2.  Scegliere **Mostra origini dati** dal menu **Dati**.

3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4.  Fare clic su **oggetto** nel **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

5.  Espandere i nodi, quindi individuare e selezionare la classe.

    > [!NOTE]
    >  Se il **cliente** classe non è disponibile, annullare la procedura guidata, compilare il progetto e rieseguire la procedura guidata.

6.  Fare clic su **Finish** per creare l'origine dati e aggiungere il **cliente** classe di entità per il **Zdroje dat** finestra.

7.  Trascinare gli elementi dal **Zdroje dat** finestra in un form.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [LINQ al modello a oggetti SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)