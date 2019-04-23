---
title: 'Procedura: Creare classi LINQ to SQL mappate a tabelle e viste (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1b9fb62fe3b6d92c617fc89f083aadcd262579e4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055925"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: Creare classi LINQ to SQL mappate a tabelle e viste (Object Relational Designer)

Le classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping a tabelle e viste di database sono dette *classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità che si basano su viste o tabelle di database trascinando le tabelle o viste dal **Esplora Server** oppure **Esplora Database** nel [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Il **O/R Designer** genera le classi e applica le specifiche [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gli attributi per abilitare [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funzionalità (la comunicazione dei dati e le funzionalità di modifica il <xref:System.Data.Linq.DataContext>). Per informazioni dettagliate sui [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] le classi, vedere [LINQ al modello a oggetti SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
> Il **O/R Designer** è un mapper relazionale a oggetti semplice, perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

Trascinamento di tabelle o viste dal **Esplora Server** o **Esplora Database** nel **O/R Designer** consente di creare classi di entità oltre al <xref:System.Data.Linq.DataContext> metodi che vengono usati per eseguire gli aggiornamenti.

Per impostazione predefinita, il runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se questo comportamento non è quello voluto, è possibile configurare una classe di entità in modo che usi stored procedure per l'esecuzione di istruzioni di inserimento, aggiornamento ed eliminazione anziché usare il comportamento di runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] predefinito. Per altre informazioni, vedere [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

1. In **Esplora server**/**Esplora database** espandere **Tabelle** o **Viste** e individuare la tabella o la vista di database da usare nell'applicazione.

2. Trascinare la tabella o la visualizzazione nel **O/R Designer**.

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creare l'origine dati di un oggetto e visualizzare i dati in un form

Dopo aver creato le classi di entità usando il **O/R Designer**, è possibile creare un'origine dati oggetto e popolare le [finestra Origini dati](add-new-data-sources.md#data-sources-window) con le classi di entità.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare il progetto.

2. Per aprire la **Zdroje dat** finestra via il **Data** dal menu fare clic su **Mostra origini dati**.

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

5. Espandere i nodi, quindi individuare e selezionare la classe.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.

6. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

7. Trascinare gli elementi dalla finestra **Origini dati** in un form.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modello a oggetti LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Procedura dettagliata: Personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)