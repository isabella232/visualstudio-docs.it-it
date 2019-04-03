---
title: Creare e configurare i set di dati
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b71d4b8ea58cbbe36e3fe48228789d4aee02af53
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790862"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Creare e configurare i set di dati in Visual Studio

Un set di dati è un set di oggetti che archiviano i dati da un database in memoria e supportano il rilevamento delle modifiche per consentire di creare, leggere, aggiornare ed eliminazione (CRUD) sui dati senza la necessità di essere sempre connessi al database. I set di dati sono stati progettati per semplice *form over data* applicazioni aziendali. Per le nuove applicazioni, è consigliabile usare Entity Framework per archiviare e modellare i dati in memoria. Per lavorare con i set di dati, si deve avere una conoscenza di base dei concetti relativi ai database.

È possibile creare un oggetto tipizzato <xref:System.Data.DataSet> classe in Visual Studio in fase di progettazione utilizzando il **configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere [creando un dataset (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati usando la configurazione guidata origine dati

1. Aprire il progetto in Visual Studio e quindi scegliere **Project** > **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.

2. Scegliere il tipo di origine dati a cui si sarà la connessione.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

3. Scegliere uno o più database che fungerà da origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png)

4. Scegliere le tabelle o le singole colonne, stored procedure, funzioni e viste dal database che si desidera essere rappresentato nel set di dati.

     ![Scegliere gli oggetti di database](../data-tools/media/raddata-chose-objects.png)

5. Scegliere **Fine**.

   Il set di dati viene visualizzato come nodo in **Esplora soluzioni**.

   ![Set di dati in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png)

6. Fare clic sul nodo del set di dati in **Esplora soluzioni** per aprire il dataset nella cache le **Progettazione DataSet**. Ogni tabella nel set di dati è associato un `TableAdapter` oggetto, che è rappresentata nella parte inferiore. L'adattatore di tabella viene utilizzato per popolare il set di dati e, facoltativamente, per inviare comandi al database.

   ![Progettazione DataSet](../data-tools/media/dataset-designer.png)

7. Le linee di relazione che si connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli di chiave esterna in un database sono rappresentati come una relazione solo con l'aggiornamento ed eliminare le regole impostate su none. In genere, che è quello desiderato. Tuttavia, è possibile fare clic per visualizzare le righe di **relazione** finestra di dialogo in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per altre informazioni, vedere [relazioni nei DataSet](../data-tools/relationships-in-datasets.md) e [aggiornamento gerarchico](../data-tools/hierarchical-update.md).

     ![Finestra di dialogo relazione DataSet](../data-tools/media/raddata-relation-dialog.png)

8. Fare clic su una tabella, l'adattatore di tabella o nome di colonna in una tabella per visualizzarne le proprietà nel **proprietà** finestra. È possibile modificare alcuni dei valori qui. È importante ricordare che si modifica il set di dati, non il database di origine.

     ![Proprietà delle colonne di set di dati](../data-tools/media/dataset-column-properties.png)

9. È possibile aggiungere nuove tabelle o gli adattatori di tabella per il set di dati o aggiungere nuove query per gli adattatori di tabella esistente o specificare nuove relazioni tra tabelle trascinando gli elementi dal **casella degli strumenti** scheda. Questa scheda viene visualizzato quando la **Progettazione DataSet** presenta lo stato attivo.

     ![Set di dati della casella degli strumenti](../data-tools/media/raddata-dataset-toolbox.png)

Successivamente, è possibile specificare la modalità popolare il set di dati con i dati. A tal fine, si utilizza il **configurazione guidata TableAdapter**. Per altre informazioni, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati

Questa procedura viene illustrato come aggiungere una tabella dallo stesso database usato per creare innanzitutto il set di dati.

1. Fare clic sul nodo del set di dati in **Esplora soluzioni** per visualizzare i **Progettazione DataSet** messa a fuoco.

2. Fare clic sui **Zdroje dat** scheda nel margine sinistro di Visual Studio, o inserire **zdroje dat** nella casella di ricerca.

3. Il nodo di set di dati e scegliere **Configura origine dati con Creazione guidata**.

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png)

4. Utilizzare la procedura guidata per specificare quali altre tabelle, stored procedure o altri oggetti di database da aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonomo a un set di dati

1. Aprire il set di dati in **Progettazione DataSet**.

2. Trascinare un <xref:System.Data.DataTable> classe il **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.

3. Aggiungere colonne per definire la tabella di dati. Fare clic sulla tabella e scegliere **Add** > **colonna**. Usare la **proprietà** finestra per impostare il tipo di dati della colonna e una chiave, se necessario.

Le tabelle autonome devono implementare `Fill` per la logica nelle tabelle autonome in modo che è possibile inserire i dati. Per informazioni su come inserire le tabelle di dati autonomo, vedere [popolamento di un set di dati da un oggetto DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)