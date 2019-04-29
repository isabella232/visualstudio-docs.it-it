---
title: 'Procedura dettagliata: Creazione di un set di dati con Progettazione Dataset'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f91c24885cc6817889671dd7a1a6e7e1686ce93f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565000"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Procedura dettagliata: Creare un set di dati con Progettazione Dataset

In questa procedura dettagliata viene creato un set di dati usando il **Progettazione Dataset**. L'articolo illustra il processo di creazione di un nuovo progetto e aggiunta di una nuova **set di dati** elemento ad esso. Si apprenderà come creare le tabelle basate su tabelle in un database senza usare una procedura guidata.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione di Visual Studio Express LocalDB di SQL Server può essere installato come parte di **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo qualche istante, la query viene completata l'esecuzione e viene creato il database Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Creare un nuovo progetto di applicazione Windows Form

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **nome DatasetDesignerWalkthrough**, quindi scegliere **OK**.

     Visual Studio aggiunge il progetto **Esplora soluzioni** e visualizzare un nuovo form nella finestra di progettazione.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

2. Nel riquadro di sinistra, selezionare **Data**, quindi selezionare **DataSet** nel riquadro centrale.

3. Nome del set di dati **NorthwindDataset**, quindi scegliere **Add**.

     Visual Studio aggiunge un file denominato **NorthwindDataSet. xsd** al progetto e lo apre nella **Progettazione Dataset**.

## <a name="create-a-data-connection-in-server-explorer"></a>Creare una connessione dati in Esplora Server

1. Scegliere **Esplora server** dal menu **Visualizza**.

2. Nelle **Esplora Server**, fare clic sui **Connetti al Database** pulsante.

3. Creare una connessione al database di esempio Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Creare le tabelle nel set di dati

Questa sezione viene illustrato come aggiungere tabelle al set di dati.

### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers

1. Espandere la connessione dati creata nella **Esplora Server**, quindi espandere il **tabelle** nodo.

2. Trascinare il **clienti** tabella dal **Esplora Server** nel **Progettazione Dataset**.

     Oggetto **clienti** tabella dei dati e **CustomersTableAdapter** vengono aggiunti al set di dati.

### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders

- Trascinare il **ordini** tabella dal **Esplora Server** nel **Progettazione Dataset**.

     Un' **ordini** tabella di dati **OrdersTableAdapter**e relazione dati tra il **clienti** e **ordini** tabelle vengono aggiunte al set di dati.

### <a name="to-create-the-orderdetails-table"></a>Per creare la tabella OrderDetails

- Trascinare il **Order Details** tabella dal **Esplora Server** nel **Progettazione Dataset**.

     Un' **Order Details** tabella di dati **OrderDetailsTableAdapter**e una relazione dati tra il **ordini** e **OrderDetails** tabelle vengono aggiunti al set di dati.

## <a name="next-steps"></a>Passaggi successivi

- Salvare il set di dati.

- Selezionare gli elementi di **Zdroje dat** finestra e trascinarli in un form. Per altre informazioni, vedere [controlli di associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Aggiungere più query per gli oggetti TableAdapter.

- Aggiungere la logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> eventi delle tabelle di dati nel set di dati. Per altre informazioni, vedere [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Vedere anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](../data-tools/validate-data-in-datasets.md)