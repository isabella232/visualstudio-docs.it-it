---
title: Creare un set di dati con l'Progettazione DataSet
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 20cd8bdc4f7d72cd0ed3920f75a4955ee57d2a68
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036782"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Procedura dettagliata: creare un set di dati con l'Progettazione DataSet

In questa procedura dettagliata viene creato un set di dati usando il **Progettazione DataSet**. Questo articolo illustra il processo di creazione di un nuovo progetto e di aggiunta di un nuovo elemento del **set di dati** . Verrà illustrato come creare tabelle basate su tabelle in un database senza utilizzare una procedura guidata.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel Programma di installazione di Visual Studio SQL Server Express database locale può essere installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Creare un nuovo progetto di applicazione Windows Form

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Forms** .

4. Denominare il progetto **DatasetDesignerWalkthrough**, quindi scegliere **OK**.

     Visual Studio aggiunge il progetto a **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro a sinistra selezionare **dati**, quindi selezionare **DataSet** nel riquadro centrale.

3. Denominare DataSet **NorthwindDataSet**, quindi scegliere **Aggiungi**.

     Visual Studio aggiunge un file denominato **NorthwindDataSet. xsd** al progetto e lo apre nell' **Progettazione DataSet**.

## <a name="create-a-data-connection-in-server-explorer"></a>Creare una connessione dati in Esplora server

1. Scegliere **Esplora server** dal menu **Visualizza**.

2. In **Esplora server**fare clic sul pulsante **Connetti al database** .

3. Creare una connessione al database di esempio Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Creare le tabelle nel set di dati

In questa sezione viene illustrato come aggiungere tabelle al set di dati.

### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers

1. Espandere la connessione dati creata in **Esplora server**, quindi espandere il nodo **tabelle** .

2. Trascinare la tabella **Customers** da **Esplora server** nel **Progettazione DataSet**.

     Al set di dati vengono aggiunte una tabella dati **Customers** e **CustomersTableAdapter** .

### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders

- Trascinare la tabella **Orders** da **Esplora server** nel **Progettazione DataSet**.

     Al set di dati vengono aggiunte una tabella di dati **Orders** , **OrdersTableAdapter**e una relazione tra le tabelle **Customers** e **Orders** .

### <a name="to-create-the-orderdetails-table"></a>Per creare la tabella OrderDetails

- Trascinare la tabella **Order Details** da **Esplora server** nel **Progettazione DataSet**.

     Una tabella dati **Order Details** , **OrderDetailsTableAdapter**, e una relazione dati tra le tabelle **Orders** e **OrderDetails** vengono aggiunte al set di dati.

## <a name="next-steps"></a>Passaggi successivi

- Salvare il set di dati.

- Selezionare gli elementi nella finestra **origini dati** e trascinarli in un modulo. Per altre informazioni, vedere [associare Windows Forms controlli ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Aggiungere altre query agli oggetti TableAdapter.

- Aggiungere la logica di convalida <xref:System.Data.DataTable.ColumnChanging> agli <xref:System.Data.DataTable.RowChanging> eventi o delle tabelle dati nel DataSet. Per altre informazioni, vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](../data-tools/validate-data-in-datasets.md)
