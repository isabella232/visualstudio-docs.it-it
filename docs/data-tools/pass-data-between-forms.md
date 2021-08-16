---
title: Passare dati da un form all'altro
description: In questa Windows procedura dettagliata sui controlli Form vengono fornite istruzioni dettagliate per il passaggio di dati da un form a un altro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6e6fff43784338d52abecf29e889aafdc095c80771683656a11670f37ed6fa28
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347012"
---
# <a name="pass-data-between-forms"></a>Passare dati da un form all'altro

Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Usando le tabelle customers e orders di Northwind, un modulo consente agli utenti di selezionare un cliente e un secondo modulo visualizza gli ordini del cliente selezionato. Questa procedura dettagliata illustra come creare un metodo nel secondo form che riceve i dati dal primo form.

> [!NOTE]
> Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per il passaggio di dati a un form, tra cui la creazione di un secondo costruttore per ricevere dati o la creazione di una proprietà pubblica che può essere impostata con i dati del primo form.

Le attività illustrate nella procedura dettagliata sono le seguenti:

- Creazione di un nuovo **Windows di applicazione Form.**

- Creazione e configurazione di un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Selezione del controllo da creare nel form durante il trascinamento di elementi dalla finestra **Origini dati**. Per altre informazioni, vedere [Impostare il controllo da creare quando si trascina dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creazione del controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.

- Creazione di un secondo form con una griglia per la visualizzazione dei dati.

- Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.

- Passaggio dei dati da un form all'altro.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** Nell'Programma di installazione di Visual Studio, SQL Server Express Local DB può essere installato come parte del  carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la finestra **SQL Server Esplora oggetti** dati. (SQL Server Esplora oggetti viene installato come parte del carico **di** lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo. Fare clic con il pulsante destro del mouse Local DB'istanza e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="create-the-windows-forms-app-project"></a>Creare il progetto Windows'app Forms

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop.**

3. Nel riquadro centrale selezionare il tipo di **progetto Windows app Forms.**

4. Assegnare al **progetto il nome PassingDataBetweenForms** e quindi scegliere **OK.**

     Il progetto **PassingDataBetweenForms** verrà creato e aggiunto a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

1. Per aprire la **finestra Origini** dati , **scegliere** Mostra origini dati dal menu **Dati**.

2. Nella finestra **Origini dati** selezionare Aggiungi nuova **origine dati** per avviare la Configurazione **guidata origine** dati.

3. Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4. Nella pagina **Scegli modello database** verificare che sia specificato **Dataset**, quindi scegliere **Avanti**.

5. Nella pagina **Scegliere la connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

6. Se per il database è necessaria una password ed è selezionata l'opzione per l'inclusione dei dati sensibili, selezionare l'opzione e fare clic su **Avanti**.

7. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti.**

8. Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

9. Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle **Customers** e **Orders** vengono visualizzate nella finestra **Origini dati**.

## <a name="create-the-first-form-form1"></a>Creare il primo modulo (Form1)

È possibile creare una griglia con associazione a dati, ovvero un controllo <xref:System.Windows.Forms.DataGridView> trascinando il nodo **Customers** dalla finestra **Origini dati** nel form.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form

- Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     In **Form1** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form"></a>Creare il secondo modulo

Creare un secondo modulo a cui passare i dati.

1. Scegliere **Aggiungi Windows Form** dal menu **Progetto**.

2. Lasciare il nome predefinito **Form2** e scegliere **Aggiungi**.

3. Trascinare il nodo **Orders** principale dalla finestra **Origini dati** a **Form2**.

     In **Form2** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

4. Eliminare l'oggetto **OrdersBindingNavigator** dalla barra dei componenti.

     **OrdersBindingNavigator** scompare da **Form2**.

## <a name="add-a-tableadapter-query"></a>Aggiungere una query TableAdapter

Aggiungere una query TableAdapter a Form2 per caricare gli ordini per il cliente selezionato in Form1.

1. Fare doppio clic sul file **NorthwindDataSet.xsd** in **Esplora soluzioni**.

2. Fare clic con il pulsante destro del mouse su **OrdersTableAdapter** e selezionare **Aggiungi query**.

3. Lasciare l'opzione predefinita di **Usa istruzioni SQL** e scegliere **Avanti**.

4. Lasciare l'opzione predefinita di **SELECT che restituisce righe** e scegliere **Avanti**.

5. Aggiungere una clausola WHERE alla query per restituire gli `Orders` in base al `CustomerID`. La query dovrebbe essere simile alla seguente:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.

6. Fare clic su **Avanti**.

7. Per il **campo Fill a DataTableMethod Name (Compila nome metodo DataTable)** digitare `FillByCustomerID` .

8. Deselezionare l'opzione **Restituisci una DataTable**, quindi scegliere **Avanti**.

9. Fare clic su **Fine**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo in Form2 a cui passare i dati

1. Fare clic con il pulsante destro del mouse su **Form2** e selezionare **Visualizza codice** per aprire **Form2** nell'**editor di codice**.

2. Aggiungere il codice riportato di seguito a **Form2** dopo il metodo `Form2_Load`:

:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb" id="Snippet1":::
:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs" id="Snippet1":::

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo in Form1 per passare i dati e visualizzare Form2

1. In **Form1** fare clic con il pulsante destro del mouse sulla griglia dati del cliente, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** fare clic su **Eventi**.

3. Fare doppio clic sull'evento **CellDoubleClick**.

     Verrà visualizzato l'editor del codice.

4. Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet2":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet2":::

## <a name="run-the-app"></a>Eseguire l'app

- Premere **F5 per** eseguire l'applicazione.

- Fare doppio clic sul record di un cliente in **Form1** per aprire **Form2** e visualizzare gli ordini di quel cliente.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Aggiunta di funzionalità per il salvataggio dei dati nel database. Per altre informazioni, vedere [Salvare di nuovo i dati nel database.](../data-tools/save-data-back-to-the-database.md)

## <a name="see-also"></a>Vedi anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
