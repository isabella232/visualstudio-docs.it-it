---
title: Creare e configurare i set di dati
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8222b1985ab7f765be9b06fdd6abf7cb1e1cb2dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586913"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Procedura: creare e configurare DataSet in Visual Studio

Un set di dati è un set di oggetti che archivia i dati da un database in memoria e supporta il rilevamento delle modifiche per abilitare le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) su tali dati senza la necessità di essere sempre connessi al database. I set di dati sono stati progettati per semplici *forme su* applicazioni aziendali di dati. Per le nuove applicazioni, è consigliabile usare Entity Framework per archiviare e modellare i dati in memoria. Per utilizzare i set di dati, è necessario disporre di una conoscenza di base dei concetti relativi ai database.

È possibile creare una classe <xref:System.Data.DataSet> tipizzata in Visual Studio in fase di progettazione tramite la **Configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere [creazione di un set di dati (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati tramite la configurazione guidata origine dati

1. Aprire il progetto in Visual Studio, quindi scegliere **progetto** > **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

2. Scegliere il tipo di origine dati a cui si connetterà.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png)

3. Scegliere il database o i database che saranno l'origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png)

4. Scegliere le tabelle (o singole colonne), le stored procedure, le funzioni e le viste del database che si desidera rappresentare nel set di dati.

     ![Scegliere gli oggetti di database](../data-tools/media/raddata-chose-objects.png)

5. Scegliere **Fine**.

   Il set di dati viene visualizzato come nodo in **Esplora soluzioni**.

   ![Set di dati in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png)

6. Fare clic sul nodo set di dati in **Esplora soluzioni** per aprire il set di dati in **Progettazione DataSet**. A ogni tabella del set di dati è associato un oggetto `TableAdapter`, rappresentato in basso. L'adapter Table viene utilizzato per popolare il set di dati e, facoltativamente, per inviare comandi al database.

   ![Progettazione DataSet](../data-tools/media/dataset-designer.png)

7. Le linee di relazione che connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli FOREIGN KEY in un database sono rappresentati solo come relazione, con le regole Update e Delete impostate su None. In genere, questo è quello che si desidera. Tuttavia, è possibile fare clic sulle linee per visualizzare la finestra di dialogo **relazione** , in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per altre informazioni, vedere [relazioni nei set](../data-tools/relationships-in-datasets.md) di dati e [aggiornamento gerarchico](../data-tools/hierarchical-update.md).

     ![Finestra di dialogo relazione DataSet](../data-tools/media/raddata-relation-dialog.png)

8. Fare clic su una tabella, un adattatore di tabella o un nome di colonna in una tabella per visualizzarne le proprietà nella finestra **Proprietà** . È possibile modificare alcuni dei valori qui. È sufficiente ricordare che si sta modificando il set di dati, non il database di origine.

     ![Proprietà colonna DataSet](../data-tools/media/dataset-column-properties.png)

9. È possibile aggiungere nuove tabelle o adattatori di tabella al set di dati o aggiungere nuove query per gli adattatori di tabella esistenti oppure specificare nuove relazioni tra le tabelle trascinando tali elementi dalla scheda **casella degli strumenti** . Questa scheda viene visualizzata quando **Progettazione DataSet** si trova nello stato attivo.

     ![Casella degli strumenti DataSet](../data-tools/media/raddata-dataset-toolbox.png)

Successivamente, potrebbe essere necessario specificare come popolare il set di dati con i dati. A tale proposito, utilizzare la **Configurazione guidata TableAdapter**. Per ulteriori informazioni, vedere [Fill DataSets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati esistente

In questa procedura viene illustrato come aggiungere una tabella dallo stesso database utilizzato per creare prima il set di dati.

1. Fare clic sul nodo set di dati in **Esplora soluzioni** per attivare lo stato attivo della **finestra di progettazione DataSet** .

2. Fare clic sulla scheda **origini dati** nel margine sinistro di Visual Studio oppure digitare **origini dati** nella casella di ricerca.

3. Fare clic con il pulsante destro del mouse sul nodo DataSet e scegliere **Configura origine dati con la procedura guidata**.

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png)

4. Utilizzare la procedura guidata per specificare le tabelle, le stored procedure o altri oggetti di database aggiuntivi da aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonoma a un set di dati

1. Aprire il set di dati in **Progettazione DataSet**.

2. Trascinare una classe <xref:System.Data.DataTable> dalla scheda **DataSet** della **casella degli strumenti** nel **Progettazione DataSet**.

3. Aggiungere colonne per definire la tabella di dati. Fare clic con il pulsante destro del mouse sulla tabella e scegliere **aggiungi** > **colonna**. Utilizzare la finestra **Proprietà** per impostare il tipo di dati della colonna e una chiave, se necessario.

Le tabelle autonome devono implementare `Fill` logica in tabelle autonome in modo da poterle inserire i dati. Per informazioni sul riempimento di tabelle di dati autonome, vedere [popolamento di un DataSet da un oggetto DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
