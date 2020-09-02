---
title: Passare dati tra moduli | Microsoft Docs
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e14165ba2111f40898c00b3d01950425c042070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652916"
---
# <a name="pass-data-between-forms"></a>Passare dati da un form all'altro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Utilizzando le tabelle Customers e Orders di Northwind, un modulo consente agli utenti di selezionare un cliente e un secondo modulo Visualizza gli ordini del cliente selezionato. In questa procedura dettagliata viene illustrato come creare un metodo nel secondo form che riceve i dati dal primo form.

> [!NOTE]
> Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per il passaggio di dati a un modulo, tra cui la creazione di un secondo costruttore per la ricezione dei dati o la creazione di una proprietà pubblica che può essere impostata con i dati del primo form.

 Le attività illustrate nella procedura dettagliata sono le seguenti:

- Creazione di un nuovo progetto di **applicazione Windows** .

- Creazione e configurazione di un set di [dati con la configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Selezione del controllo da creare nel form durante il trascinamento di elementi dalla finestra **Origini dati**. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creazione del controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.

- Creazione di un secondo form con una griglia per la visualizzazione dei dati.

- Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.

- Passaggio dei dati da un form all'altro.

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario:

- Accedere al database di esempio Northwind.

## <a name="create-the-windows-application"></a>Creare l'applicazione Windows

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. Creare un nuovo progetto dal menu **file** .

2. Assegnare al progetto il nome `PassingDataBetweenForms`.

3. Selezionare **Windows Forms applicazione**e fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto **PassingDataBetweenForms** verrà creato e aggiunto a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Mostra origini dati** dal menu **Dati**.

2. Nella finestra **origini dati** selezionare **Aggiungi nuova origine dati** per avviare la configurazione guidata **origine dati** .

3. Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4. Nella pagina **Scegli modello database** verificare che sia specificato **Dataset**, quindi scegliere **Avanti**.

5. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

6. Se per il database è necessaria una password ed è selezionata l'opzione per l'inclusione dei dati sensibili, selezionare l'opzione e fare clic su **Avanti**.

7. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.

8. Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

9. Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle **Customers** e **Orders** vengono visualizzate nella finestra **Origini dati**.

## <a name="create-the-first-form-form1"></a>Creare il primo form (Form1)
 È possibile creare una griglia con associazione a dati, ovvero un controllo <xref:System.Windows.Forms.DataGridView> trascinando il nodo **Customers** dalla finestra **Origini dati** nel form.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form

- Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     In **Form1** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

## <a name="create-the-second-form-form2"></a>Creare il secondo form (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Per creare un secondo form al quale passare i dati

1. Scegliere **Aggiungi Windows Form** dal menu **Progetto**.

2. Lasciare il nome predefinito **Form2** e scegliere **Aggiungi**.

3. Trascinare il nodo **Orders** principale dalla finestra **Origini dati** a **Form2**.

     In **Form2** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

4. Eliminare l'oggetto **OrdersBindingNavigator** dalla barra dei componenti.

     **OrdersBindingNavigator** scompare da **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Aggiungere una query TableAdapter a Form2 per caricare gli ordini per il cliente selezionato in Form1

#### <a name="to-create-a-tableadapter-query"></a>Per creare una query TableAdapter

1. Fare doppio clic sul file **NorthwindDataSet.xsd** in **Esplora soluzioni**.

2. Fare clic con il pulsante destro del mouse su **OrdersTableAdapter** e selezionare **Aggiungi query**.

3. Lasciare l'opzione predefinita di **Usa istruzioni SQL** e scegliere **Avanti**.

4. Lasciare l'opzione predefinita di **SELECT che restituisce righe** e scegliere **Avanti**.

5. Aggiungere una clausola WHERE alla query per restituire gli `Orders` in base al `CustomerID`. La query dovrebbe essere simile alla seguente:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.

6. Fare clic su **Avanti**.

7. Per il **riempimento di un nome DataTableMethod**, digitare `FillByCustomerID` .

8. Deselezionare l'opzione **Restituisci una DataTable**, quindi scegliere **Avanti**.

9. Fare clic su **Fine**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo su Form2 per passare i dati a

#### <a name="to-create-a-method-to-pass-data-to"></a>Per creare un metodo al quale passare i dati

1. Fare clic con il pulsante destro del mouse su **Form2** e selezionare **Visualizza codice** per aprire **Form2** nell'**editor di codice**.

2. Aggiungere il codice riportato di seguito a **Form2** dopo il metodo `Form2_Load`:

     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo in Form1 per passare i dati e visualizzare Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Per creare un metodo per il passaggio dei dati a Form2

1. In **Form1** fare clic con il pulsante destro del mouse sulla griglia dati del cliente, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** fare clic su **Eventi**.

3. Fare doppio clic sull'evento **CellDoubleClick**.

     Verrà visualizzato l'editor del codice.

4. Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:

     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]

## <a name="run-the-application"></a>Eseguire l'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

- Premere F5 per eseguire l'applicazione.

- Fare doppio clic sul record di un cliente in **Form1** per aprire **Form2** e visualizzare gli ordini di quel cliente.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

- Aggiunta di funzionalità per il salvataggio dei dati nel database. Per altre informazioni, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Vedere anche
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
