---
title: Creare un set di dati con il Progettazione DataSet
description: In questa procedura dettagliata viene creato un set di dati usando il Progettazione DataSet. Comprendere il processo di creazione di un nuovo progetto e l'aggiunta di un nuovo elemento DataSet.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d502812179b0449c2dca6be800f69c30d211a28b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059190"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Procedura dettagliata: Creare un set di dati con il Progettazione DataSet

In questa procedura dettagliata viene creato un set di dati usando **Progettazione DataSet**. L'articolo illustra il processo di creazione di un nuovo progetto e l'aggiunta di un nuovo **elemento DataSet.** Si apprenderà come creare tabelle basate su tabelle in un database senza usare una procedura guidata.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** Nell'Programma di installazione di Visual Studio, SQL Server Express Local DB può essere installato come parte del  carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la finestra **SQL Server Esplora oggetti** dati. (SQL Server Esplora oggetti viene installato come parte del carico **di** lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo. Fare clic con il pulsante destro del mouse sull Local DB e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="create-a-new-windows-forms-application-project"></a>Creare un nuovo progetto di applicazione Windows Form

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** **o Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop.**

3. Nel riquadro centrale selezionare il tipo di **progetto Windows app Forms.**

4. Assegnare al progetto **il nome DatasetDesignerWalkthrough** e quindi scegliere **OK.**

     Visual Studio aggiunge il progetto a **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro sinistro selezionare Dati **e** quindi Selezionare **DataSet** nel riquadro centrale.

3. Assegnare al set **di dati il nome NorthwindDataset** e quindi scegliere **Aggiungi.**

     Visual Studio aggiunge un file **denominato NorthwindDataset.xsd** al progetto e lo apre nel **Progettazione DataSet**.

## <a name="create-a-data-connection-in-server-explorer"></a>Creare una connessione dati in Esplora server

1. Scegliere **Esplora server** dal menu **Visualizza**.

2. In **Esplora server** fare clic sul **pulsante Connessione al database** .

3. Creare una connessione al database di esempio Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Creare le tabelle nel set di dati

In questa sezione viene illustrato come aggiungere tabelle al set di dati.

### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers

1. Espandere la connessione dati creata in **Esplora server**, quindi espandere il **nodo** Tabelle .

2. Trascinare **la tabella Customers** da **Esplora server** **nella** Progettazione DataSet .

     Una **tabella dati Customers** e **customersTableAdapter** vengono aggiunte al set di dati.

### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders

- Trascinare **la tabella Orders** **Esplora server** **nella** Progettazione DataSet .

     Al **set** di dati vengono aggiunte una tabella di dati **Orders, OrdersTableAdapter,** e una relazione dati tra le tabelle **Customers** e **Orders.**

### <a name="to-create-the-orderdetails-table"></a>Per creare la tabella OrderDetails

- Trascinare **la tabella Dettagli** ordine **Esplora server** **nella** Progettazione DataSet .

     Al **set di dati** vengono aggiunte una tabella di dati Order **Details, OrderDetailsTableAdapter,** e una relazione dati tra le tabelle **Orders** e **OrderDetails.**

## <a name="next-steps"></a>Passaggi successivi

- Salvare il set di dati.

- Selezionare gli elementi nella **finestra Origini** dati e trascinarli in un form. Per altre informazioni, vedere [Associare Windows form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Aggiungere altre query ai TableAdapter.

- Aggiungere la logica di convalida <xref:System.Data.DataTable.ColumnChanging> agli eventi o delle tabelle di dati nel set di <xref:System.Data.DataTable.RowChanging> dati. Per altre informazioni, vedere [Convalidare i dati nei set di dati.](../data-tools/validate-data-in-datasets.md)

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalidare i dati](../data-tools/validate-data-in-datasets.md)
