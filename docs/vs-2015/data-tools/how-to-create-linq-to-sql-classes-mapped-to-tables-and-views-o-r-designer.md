---
title: 'Procedura: creare classi di LINQ to SQL mappate a tabelle e viste (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665919"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Procedura: Creare classi LINQ to SQL con mapping a tabelle e viste (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL classi di cui è stato eseguito il mapping a tabelle e viste di database sono denominate *classi di entità*. Per la classe di entità viene eseguito il mapping a un record, mentre per le singole proprietà di una classe di entità viene eseguito il mapping alle singole colonne che costituiscono un record. Creare classi di entità basate su viste o tabelle di database trascinando le tabelle o le viste da **Esplora server** /**Esplora database** sugli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] genera le classi e applica la specifica [! LINQ to SQL attributi per abilitare [! LINQ to SQL funzionalità (le funzionalità di comunicazione e modifica dei dati della <xref:System.Data.Linq.DataContext>). Per informazioni dettagliate su [! LINQ to SQL le classi, vedere [il modello a oggetti di LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è un mapper relazionale a oggetti semplice perché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, quale il mapping di una classe di entità a più tabelle, non è supportato. Tuttavia, è possibile eseguire il mapping di una classe di entità a una visualizzazione che crea un join tra più tabelle correlate.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Creazione di classi LINQ to SQL con mapping a tabelle o visualizzazioni di database
 Il trascinamento di tabelle o viste da **Esplora server** /**Esplora database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crea classi di entità oltre ai metodi di <xref:System.Data.Linq.DataContext> utilizzati per l'esecuzione degli aggiornamenti.

 Per impostazione predefinita, il valore di [! LINQ to SQL Runtime crea la logica per salvare le modifiche da una classe di entità aggiornabile nel database. Tale logica si basa sullo schema della tabella (definizioni di colonna e informazioni sulla chiave primaria). Se non si desidera questo comportamento, è possibile configurare una classe di entità in modo che utilizzi stored procedure per l'esecuzione di inserimenti, aggiornamenti ed eliminazioni anziché utilizzare l'impostazione predefinita [! Comportamento LINQ to SQL Runtime. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Per creare classi LINQ to SQL con mapping a tabelle o visualizzazioni di database

1. In **Server** /**Esplora database**espandere **tabelle** o **viste** e individuare la tabella o la vista del database che si desidera utilizzare nell'applicazione.

2. Trascinare la tabella o la visualizzazione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione. Tale classe presenta proprietà con mapping alle colonne nella tabella o visualizzazione selezionata.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Creazione dell'origine dati di un oggetto e visualizzazione dei dati in un form
 Dopo aver creato le classi di entità utilizzando la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], è possibile creare un'origine dati oggetto e popolare la [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) con le classi di entità.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Per creare l'origine dati di un oggetto in base alle classi di entità LINQ to SQL

1. Scegliere **Compila soluzione** dal menu **Compila** per compilare il progetto.

2. Scegliere **Mostra origini dati** dal menu **Dati**.

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4. Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto** e quindi su **Avanti**.

5. Espandere i nodi, quindi individuare e selezionare la classe.

    > [!NOTE]
    > Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.

6. Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.

7. Trascinare gli elementi dalla finestra **Origini dati** in un form.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: creazione di classi di LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Modello a oggetti LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Procedura dettagliata: aggiunta di convalida alle classi di entità](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)