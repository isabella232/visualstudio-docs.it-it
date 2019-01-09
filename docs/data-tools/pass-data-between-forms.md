---
title: Passare dati da un form all'altro
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 0f4c77e4d2f8d0c75f71942cf61213210bc680ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944827"
---
# <a name="pass-data-between-forms"></a>Passare dati da un form all'altro

Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Usa le tabelle customers e orders di Northwind, un unico modulo consente agli utenti di selezionare un cliente e un secondo form vengono visualizzati gli ordini del cliente selezionato. Questa procedura dettagliata viene illustrato come creare un metodo nel secondo form che riceve i dati del primo form.

> [!NOTE]
> Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per passare dati a un form, inclusa la creazione di un secondo costruttore per la ricezione di dati, o la creazione di una proprietà pubblica che può essere impostata con i dati del primo form.

Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di una nuova **Windows Forms Application** progetto.

-   Creazione e configurazione di un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

-   Selezione del controllo da creare nel form durante il trascinamento di elementi dalla finestra **Origini dati**. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creazione del controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.

-   Creazione di un secondo form con una griglia per la visualizzazione dei dati.

-   Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.

-   Passaggio dei dati da un form all'altro.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione di Visual Studio Express LocalDB di SQL Server può essere installato come parte di **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-the-windows-forms-app-project"></a>Creare il progetto di app di Windows Form

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual C#**  oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Desktop di Windows**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **PassingDataBetweenForms**, quindi scegliere **OK**.

     Il progetto **PassingDataBetweenForms** verrà creato e aggiunto a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

1.  Per aprire la **Zdroje dat** finestra via il **Data** dal menu fare clic su **Mostra origini dati**.

2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nella pagina **Scegli modello database** verificare che sia specificato **Dataset**, quindi scegliere **Avanti**.

5.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

6.  Se per il database è necessaria una password ed è selezionata l'opzione per l'inclusione dei dati sensibili, selezionare l'opzione e fare clic su **Avanti**.

7.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

8.  Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

9. Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle **Customers** e **Orders** vengono visualizzate nella finestra **Origini dati**.

## <a name="create-the-first-form-form1"></a>Creare il primo form (Form1)

È possibile creare una griglia con associazione a dati, ovvero un controllo <xref:System.Windows.Forms.DataGridView> trascinando il nodo **Customers** dalla finestra **Origini dati** nel form.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form

-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     In **Form1** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form"></a>Creare la seconda forma

Creare un secondo form per passare i dati.

1.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.

2.  Lasciare il nome predefinito **Form2** e scegliere **Aggiungi**.

3.  Trascinare il nodo **Orders** principale dalla finestra **Origini dati** a **Form2**.

     In **Form2** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

4.  Eliminare l'oggetto **OrdersBindingNavigator** dalla barra dei componenti.

     **OrdersBindingNavigator** scompare da **Form2**.

## <a name="add-a-tableadapter-query"></a>Aggiungere una query TableAdapter

Aggiungere una query TableAdapter a Form2 per caricare gli ordini del cliente selezionato nel Form1.

1.  Fare doppio clic sul file **NorthwindDataSet.xsd** in **Esplora soluzioni**.

2.  Fare clic con il pulsante destro del mouse su **OrdersTableAdapter** e selezionare **Aggiungi query**.

3.  Lasciare l'opzione predefinita di **Usa istruzioni SQL** e scegliere **Avanti**.

4.  Lasciare l'opzione predefinita di **SELECT che restituisce righe** e scegliere **Avanti**.

5.  Aggiungere una clausola WHERE alla query per restituire gli `Orders` in base al `CustomerID`. La query dovrebbe essere simile alla seguente:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.

6.  Scegliere **Avanti**.

7.  Per il **inserire un nome DataTableMethod**, tipo `FillByCustomerID`.

8.  Deselezionare l'opzione **Restituisci una DataTable**, quindi scegliere **Avanti**.

9. Scegliere **Fine**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo su Form2 al quale passare i dati

1.  Fare clic con il pulsante destro del mouse su **Form2** e selezionare **Visualizza codice** per aprire **Form2** nell'**editor di codice**.

2.  Aggiungere il codice riportato di seguito a **Form2** dopo il metodo `Form2_Load`:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo su Form1 per passare i dati e visualizzare Form2

1.  In **Form1** fare clic con il pulsante destro del mouse sulla griglia dati del cliente, quindi scegliere **Proprietà**.

2.  Nella finestra **Proprietà** fare clic su **Eventi**.

3.  Fare doppio clic sull'evento **CellDoubleClick**.

     Verrà visualizzato l'editor del codice.

4.  Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Eseguire l'app

-   Premere **F5** per eseguire l'applicazione.

-   Fare doppio clic sul record di un cliente in **Form1** per aprire **Form2** e visualizzare gli ordini di quel cliente.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

-   Aggiunta di funzionalità per il salvataggio dei dati nel database. Per altre informazioni, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)