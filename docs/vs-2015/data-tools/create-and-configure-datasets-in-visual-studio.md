---
title: Creare e configurare i set di dati
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72631199"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Creare e configurare i set di dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *set di dati è un* set di oggetti che archivia i dati da un database in memoria e supporta il rilevamento delle modifiche per abilitare le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) su tali dati senza la necessità di essere sempre connessi al database. I set di dati sono stati progettati per semplici *forme su* applicazioni aziendali di dati. Per le nuove applicazioni, è consigliabile usare Entity Framework per archiviare e modellare i dati in memoria. Per utilizzare i set di dati, è necessario disporre di una conoscenza di base dei concetti relativi ai database.

 Per creare una classe <xref:System.Data.DataSet> tipizzata in Visual Studio in fase di progettazione, utilizzare la **Configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere [creazione di un set di dati](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati tramite la configurazione guidata origine dati

1. Scegliere **Aggiungi nuova origine dati** dal menu **progetto** per avviare la **Configurazione guidata origine dati**.

2. Scegliere il tipo di origine dati a cui ci si connetterà.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png "Configurazione guidata origine dati")

3. Per i database, scegliere il database o i database che saranno l'origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png "Origine dati scegliere una connessione")

4. Scegliere le tabelle (o singole colonne), le stored procedure, le funzioni e le viste del database che si desidera rappresentare nel set di dati.

     ![Selezione oggetti di database](../data-tools/media/raddata-chose-objects.png "raddata sceglie oggetti")

5. Scegliere **Fine**.

6. Il set di dati viene visualizzato come nodo in **Esplora soluzioni**:

     ![Set di dati in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png "Set di dati in Esplora soluzioni")

     Fare clic su tale nodo per visualizzare il set di dati in **Progettazione DataSet**. Si noti che a ogni tabella del set di dati è associato un oggetto TableAdapter, rappresentato in basso. L'adapter Table viene utilizzato per popolare il set di dati e, facoltativamente, per inviare comandi al database.

     ![Progettazione DataSet](../data-tools/media/dataset-designer.png "Progettazione DataSet")

7. Le linee di relazione che connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli FOREIGN KEY in un database sono rappresentati solo come relazione, con le regole Update e Delete impostate su None. In genere, questo è quello che si desidera. Tuttavia, è possibile fare clic sulle linee per visualizzare la finestra di dialogo **relazione** , in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per altre informazioni, vedere [relazioni nei set](../data-tools/relationships-in-datasets.md) di dati e [aggiornamento gerarchico](../data-tools/hierarchical-update.md).

     ![Finestra di dialogo relazione DataSet](../data-tools/media/raddata-relation-dialog.png "finestra di dialogo raddata relation")

8. Fare clic su una tabella, un adattatore di tabella o un nome di colonna in una tabella per visualizzarne le proprietà nella finestra **Proprietà** . È possibile modificare alcuni dei valori qui. È sufficiente ricordare che si sta modificando il set di dati, non il database di origine.

     ![Proprietà colonna DataSet](../data-tools/media/dataset-column-properties.png "Proprietà colonna DataSet")

9. È possibile aggiungere nuove tabelle o adattatori di tabella al set di dati o aggiungere nuove query per gli adattatori di tabella esistenti oppure specificare nuove relazioni tra le tabelle trascinando tali elementi dalla scheda **casella degli strumenti** . Questa scheda viene visualizzata quando **Progettazione DataSet** si trova nello stato attivo.

     ![Casella degli strumenti DataSet](../data-tools/media/raddata-dataset-toolbox.png "Casella degli strumenti del set di dati raddata")

10. Successivamente, è probabile che si desideri specificare come popolare il set di dati con i dati. A tale proposito, utilizzare la **Configurazione guidata TableAdapter**. Per ulteriori informazioni, vedere [Fill DataSets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati esistente
 In questa procedura viene illustrato come aggiungere una tabella dallo stesso database utilizzato per creare prima il set di dati.

1. Fare clic sul nodo set di dati in **Esplora soluzioni** per attivare lo stato attivo della finestra di progettazione DataSet.

2. Fare clic sulla scheda **origini dati** nel margine sinistro di Visual Studio oppure immettere `Data Sources` in **QuickLaunch**.

3. Fare clic con il pulsante destro del mouse sul nodo DataSet e scegliere **Configura origine dati con la procedura guidata** .

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png "Menu di scelta rapida origine dati")

4. Utilizzare la procedura guidata per specificare quali tabelle aggiuntive, o stored procedure o altri oggetti di database, aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonoma a un set di dati

1. Aprire il set di dati in **Progettazione DataSet**.

2. Trascinare una classe <xref:System.Data.DataTable> dalla scheda **DataSet** della **casella degli strumenti** nel **Progettazione DataSet**.

3. Aggiungere colonne per definire la tabella di dati. Per altre informazioni, vedere [procedura: aggiungere colonne a un oggetto DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Le tabelle autonome devono implementare `Fill` logica in tabelle autonome in modo da poterle inserire i dati. Per informazioni sul riempimento di tabelle di dati autonome, vedere [popolamento di un DataSet da un oggetto DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
