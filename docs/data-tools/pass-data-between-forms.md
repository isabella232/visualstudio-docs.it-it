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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 580ca6a9a384fff373a72e5449af2790a8c1e5b8
ms.sourcegitcommit: 1df0ae74af03bcf0244129a29fd6bd605efc9f61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2018
ms.locfileid: "50750761"
---
# <a name="pass-data-between-forms"></a>Passare dati da un form all'altro

Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Usa le tabelle customers e orders di Northwind, un unico modulo consente agli utenti di selezionare un cliente e un secondo form vengono visualizzati gli ordini del cliente selezionato. Questa procedura dettagliata viene illustrato come creare un metodo nel secondo form che riceve i dati del primo form.

> [!NOTE]
> Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per passare dati a un form, inclusa la creazione di un secondo costruttore per la ricezione di dati, o la creazione di una proprietà pubblica che può essere impostata con i dati del primo form.

Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di una nuova **Windows Forms Application** progetto.

-   Creazione e configurazione di un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

-   Selezione del controllo da creare nel form quando si trascinano elementi dal **Zdroje dat** finestra. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creazione di un controllo con associazione a dati trascinando elementi dal **Zdroje dat** finestra in un form.

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

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **PassingDataBetweenForms**, quindi scegliere **OK**.

     Il **PassingDataBetweenForms** progetto viene creato e aggiunto alla **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **scegliere un modello di database** verificare che **set di dati** viene specificato e quindi fare clic su **Next**.

5.  Nel **scegliere la connessione dati** pagina, effettuare una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.

6.  Se il database richiede una password e se è abilitata l'opzione per includere dati sensibili, selezionare l'opzione e quindi fare clic su **successivo**.

7.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

8.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.

9. Selezionare il **clienti** e **ordini** tabelle e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e il **clienti** e **ordini** le tabelle vengono visualizzate nel **Zdroje dat** finestra.

## <a name="create-the-first-form-form1"></a>Creare il primo form (Form1)

È possibile creare una griglia con associazione a dati (un <xref:System.Windows.Forms.DataGridView> controllo), trascinando le **clienti** nodo dal **Zdroje dat** finestra nei form.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form

-   Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei **Form1**.

     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nella **Form1**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

## <a name="create-the-second-form"></a>Creare la seconda forma

Creare un secondo form per passare i dati.

1.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.

2.  Lasciare il nome predefinito **Form2**, fare clic su **Add**.

3.  Trascinare l'oggetto principale **ordini** nodo dalle **Zdroje dat** finestra nei **Form2**.

     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nella **Form2**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

4.  Eliminare il **OrdersBindingNavigator** dalla barra dei componenti.

     Il **OrdersBindingNavigator** scompare dal **Form2**.

## <a name="add-a-tableadapter-query"></a>Aggiungere una query TableAdapter

Aggiungere una query TableAdapter a Form2 per caricare gli ordini del cliente selezionato nel Form1.

1.  Fare doppio clic il **NorthwindDataSet. xsd** del file in **Esplora soluzioni**.

2.  Fare doppio clic il **OrdersTableAdapter**e selezionare **Aggiungi Query**.

3.  Lasciare l'opzione predefinita **Usa istruzioni SQL**, quindi fare clic su **successivo**.

4.  Lasciare l'opzione predefinita **SELECT che restituisce righe**, quindi fare clic su **successivo**.

5.  Aggiungere una clausola WHERE alla query, per restituire `Orders` base il `CustomerID`. La query dovrebbe essere simile alla seguente:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.

6.  Scegliere **Avanti**.

7.  Per il **inserire un nome DataTableMethod**, tipo `FillByCustomerID`.

8.  Cancella il **Restituisci un DataTable** opzione e quindi fare clic su **successivo**.

9. Scegliere **Fine**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo su Form2 al quale passare i dati

1.  Fare doppio clic su **Form2**e selezionare **Visualizza codice** per aprire **Form2** nel **Editor di codice**.

2.  Aggiungere il codice seguente a **Form2** dopo il `Form2_Load` metodo:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo su Form1 per passare i dati e visualizzare Form2

1.  Nelle **Form1**, fare doppio clic su griglia dati del cliente e quindi fare clic su **proprietà**.

2.  Nel **delle proprietà** finestra, fare clic su **eventi**.

3.  Fare doppio clic il **CellDoubleClick** evento.

     Verrà visualizzato l'editor del codice.

4.  Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Eseguire l'app

-   Premere **F5** per eseguire l'applicazione.

-   Fare doppio clic su un record del cliente nella **Form1** per aprire **Form2** con gli ordini del cliente.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

-   Aggiunta di funzionalità per il salvataggio dei dati nel database. Per altre informazioni, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)