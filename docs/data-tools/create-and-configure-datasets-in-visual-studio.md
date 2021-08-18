---
title: Creare e configurare i set di dati
description: Creare e configurare set di dati in Visual Studio. Un set di dati è un set di oggetti che archiviano i dati di un database in memoria e supportano le operazioni CRUD su questi dati.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8ce31c2e5a7e5e5f0441c213bd3f320212de5d3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037057"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Procedura: Creare e configurare set di dati in Visual Studio

Un set di dati è un set di oggetti che archiviano i dati di un database in memoria e supportano il rilevamento delle modifiche per abilitare le operazioni CRUD (Create, Read, Update ed Delete) su questi dati senza che sia necessario essere sempre connessi al database. I set di dati sono stati progettati per *moduli semplici rispetto alle applicazioni aziendali* dei dati. Per le nuove applicazioni, è consigliabile usare Entity Framework per archiviare e modellare i dati in memoria. Per usare i set di dati, è necessario avere una conoscenza di base dei concetti relativi al database.

È possibile creare una classe <xref:System.Data.DataSet> tipiata in Visual Studio in fase di progettazione usando la **Configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere Creazione di un set di [dati (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati usando la Configurazione guidata origine dati

1. Aprire il progetto in Visual Studio e quindi scegliere Project Aggiungi nuova origine dati  >   per avviare la Configurazione guidata **origine dati**.

2. Scegliere il tipo di origine dati a cui ci si connetterà.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

3. Scegliere il database o i database che saranno l'origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png)

4. Scegliere le tabelle (o le singole colonne), le stored procedure, le funzioni e le viste del database che si desidera rappresentare nel set di dati.

     ![Scegliere gli oggetti di database](../data-tools/media/raddata-chose-objects.png)

5. Fare clic su **Fine**.

   Il set di dati viene visualizzato come nodo in **Esplora soluzioni**.

   ![DataSet in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png)

6. Fare clic sul nodo del **set Esplora soluzioni** per aprire il set di dati in **Progettazione DataSet**. A ogni tabella del set di dati è associato un `TableAdapter` oggetto , rappresentato nella parte inferiore. L'adattatore tabella viene usato per popolare il set di dati e facoltativamente per inviare comandi al database.

   ![Progettazione DataSet](../data-tools/media/dataset-designer.png)

7. Le linee di relazione che connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli di chiave esterna in un database sono rappresentati solo come relazione, con le regole di aggiornamento ed eliminazione impostate su nessuna. In genere, questo è ciò che si vuole. È tuttavia possibile fare clic sulla riga per visualizzare la finestra di dialogo **Relazione,** in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per altre informazioni, vedere [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md) e Aggiornamento [gerarchico.](../data-tools/hierarchical-update.md)

     ![Finestra di dialogo Relazione set di dati](../data-tools/media/raddata-relation-dialog.png)

8. Fare clic sul nome di una tabella, di un adattatore di tabella o di una colonna in una tabella per visualizzarne le proprietà nella **finestra** Proprietà. È possibile modificare alcuni dei valori qui. È sufficiente ricordare che si sta modificando il set di dati, non il database di origine.

     ![Proprietà della colonna DataSet](../data-tools/media/dataset-column-properties.png)

9. È possibile aggiungere nuove tabelle o adattatori di tabella al set di dati oppure aggiungere nuove query per gli adattatori di tabella esistenti oppure specificare nuove relazioni tra le tabelle trascinando tali elementi dalla scheda **Casella degli** strumenti. Questa scheda viene visualizzata quando **Progettazione DataSet è** attivo.

     ![Casella degli strumenti del set di dati](../data-tools/media/raddata-dataset-toolbox.png)

È quindi possibile specificare come popolare il set di dati con i dati. Per questo si usa la **Configurazione guidata TableAdapter**. Per altre informazioni, vedere [Riempire i set di dati tramite TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md)

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati esistente

Questa procedura illustra come aggiungere una tabella dallo stesso database usato per creare prima il set di dati.

1. Fare clic sul nodo del set **di Esplora soluzioni** per spostare lo stato attivo in **Progettazione DataSet.**

2. Fare clic **sulla scheda Origini** dati nel margine sinistro Visual Studio oppure digitare le **origini** dati nella casella di ricerca.

3. Fare clic con il pulsante destro del mouse sul nodo del set di dati e **scegliere Configura origine dati con procedura guidata**.

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png)

4. Utilizzare la procedura guidata per specificare quali tabelle, stored procedure o altri oggetti di database aggiuntivi aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonoma a un set di dati

1. Aprire il set di dati in **Progettazione DataSet**.

2. Trascinare <xref:System.Data.DataTable> una classe dalla scheda **DataSet** della Casella **degli strumenti** nella **Progettazione DataSet**.

3. Aggiungere colonne per definire la tabella dati. Fare clic con il pulsante destro del mouse sulla tabella e **scegliere Aggiungi**  >  **colonna**. Usare la **finestra** Proprietà per impostare il tipo di dati della colonna e una chiave, se necessario.

Le tabelle autonome devono implementare la logica nelle tabelle autonome in modo da `Fill` poterle riempire con dati. Per informazioni sul riempimento di tabelle di dati autonome, vedere [Popolamento di un DataSet da un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vedi anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
