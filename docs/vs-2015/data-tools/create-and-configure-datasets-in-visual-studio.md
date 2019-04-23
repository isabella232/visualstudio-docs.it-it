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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a2930acee9e187f14b87e28190a88195b0bea7a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656248"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Creare e configurare i set di dati in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oggetto *set di dati* è un set di oggetti che archiviano i dati da un database in memoria e supportano il rilevamento delle modifiche per consentire di creare, leggere, aggiornare ed eliminazione (CRUD) sui dati senza la necessità di essere sempre connessi al database. I set di dati sono stati progettati per semplice *form over data* applicazioni aziendali. Per le nuove applicazioni, è consigliabile usare Entity Framework per archiviare e modellare i dati in memoria. Per lavorare con i set di dati, si deve avere una conoscenza di base dei concetti relativi ai database.

 Si crea un oggetto tipizzato <xref:System.Data.DataSet> classe in Visual Studio in fase di progettazione utilizzando il **configurazione guidata origine dati**. Per informazioni sulla creazione di set di dati a livello di codice, vedere [creazione di un set di dati](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Creare un nuovo set di dati usando la configurazione guidata origine dati

1.  Nel **progetto** menu, fare clic su **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.

2.  Scegliere il tipo dell'origine dati che si connetterà a.

     ![Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png "configurazione guidata origine dati")

3.  Per i database, scegliere uno o più database che fungerà da origine dati per il set di dati.

     ![Origine dati scegliere una connessione](../data-tools/media/data-source-choose-a-connection.png "origine dati scegliere una connessione")

4.  Scegliere le tabelle o le singole colonne, stored procedure, funzioni e viste dal database che si desidera essere rappresentato nel set di dati.

     ![Scegli oggetti di database](../data-tools/media/raddata-chose-objects.png "raddata scegliere oggetti")

5.  Scegliere **Fine**.

6.  Il set di dati viene visualizzato come nodo in **Esplora soluzioni**:

     ![Set di dati in Esplora soluzioni](../data-tools/media/dataset-in-solution-explorer.png "set di dati in Esplora soluzioni")

     Fare clic su tale nodo, e il set di dati verrà visualizzata la **Progettazione DataSet**. Si noti che ogni tabella nel set di dati dispone di un oggetto TableAdapter associato, che è rappresentato nella parte inferiore. L'adattatore di tabella viene utilizzato per popolare il set di dati e, facoltativamente, per inviare comandi al database.

     ![Progettazione DataSet](../data-tools/media/dataset-designer.png "Progettazione DataSet")

7.  Le linee di relazione che si connettono le tabelle rappresentano le relazioni tra tabelle, come definito nel database. Per impostazione predefinita, i vincoli di chiave esterna in un database sono rappresentati come una relazione solo con l'aggiornamento ed eliminare le regole impostate su none. In genere, che è quello desiderato. Tuttavia, è possibile fare clic per visualizzare le righe di **relazione** finestra di dialogo in cui è possibile modificare il comportamento degli aggiornamenti gerarchici. Per altre informazioni, vedere [relazioni nei DataSet](../data-tools/relationships-in-datasets.md) e [aggiornamento gerarchico](../data-tools/hierarchical-update.md).

     ![Finestra di dialogo relazione DataSet](../data-tools/media/raddata-relation-dialog.png "finestra di dialogo relazione raddata")

8.  Fare clic su una tabella, l'adattatore di tabella o nome di colonna in una tabella per visualizzarne le proprietà nel **proprietà** finestra. È possibile modificare alcuni dei valori qui. È importante ricordare che si modifica il set di dati, non il database di origine.

     ![Proprietà set di dati colonna](../data-tools/media/dataset-column-properties.png "proprietà set di dati colonna")

9. È possibile aggiungere nuove tabelle o gli adattatori di tabella per il set di dati o aggiungere nuove query per gli adattatori di tabella esistente o specificare nuove relazioni tra tabelle trascinando gli elementi dal **casella degli strumenti** scheda. Questa scheda viene visualizzato quando la **Progettazione DataSet** presenta lo stato attivo.

     ![Set di dati della casella degli strumenti](../data-tools/media/raddata-dataset-toolbox.png "raddata set di dati della casella degli strumenti")

10. Successivamente, probabilmente si desidera specificare come popolare il set di dati con i dati. A tal fine, si utilizza il **configurazione guidata TableAdapter**. Per altre informazioni, vedere [compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Aggiungere una tabella di database o un altro oggetto a un set di dati
 Questa procedura viene illustrato come aggiungere una tabella dallo stesso database usato per creare innanzitutto il set di dati.

1.  Fare clic sul nodo del set di dati in **Esplora soluzioni** per rendere attivo la finestra di progettazione set di dati.

2.  Fare clic sui **Zdroje dat** scheda nel margine sinistro di Visual Studio, oppure immettere `Data Sources` nelle **avvio veloce**.

3.  Il nodo di set di dati e scegliere **Configura origine dati con Creazione guidata** .

     ![Menu di scelta rapida origine dati](../data-tools/media/data-source-context-menu.png "menu di scelta rapida Zdroj dat")

4.  Utilizzare la procedura guidata per specificare quali tabelle aggiuntive, o stored procedure o un altro oggetto di database, aggiungere al set di dati.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Aggiungere una tabella dati autonomo a un set di dati

1.  Aprire il set di dati in **Progettazione DataSet**.

2.  Trascinare un <xref:System.Data.DataTable> classe il **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.

3.  Aggiungere colonne per definire la tabella di dati. Per altre informazioni, vedere [Procedura: Aggiungere colonne a un oggetto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4.  Le tabelle autonome devono implementare `Fill` per la logica nelle tabelle autonome in modo che è possibile inserire i dati. Per informazioni su come inserire le tabelle di dati autonomo, vedere [popolamento di un set di dati da un oggetto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
