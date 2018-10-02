---
title: Passare i dati tra i form | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e046bdf38af09b5f7ea0e8beb296a2b3d32cff6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528758"
---
# <a name="pass-data-between-forms"></a>Passare dati da un form all'altro
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [passare i dati tra i form](https://docs.microsoft.com/visualstudio/data-tools/pass-data-between-forms).  
  
  
Questa procedura dettagliata fornisce istruzioni passo-passo per il passaggio dei dati da un form a un altro. Usa le tabelle customers e orders di Northwind, un unico modulo consente agli utenti di selezionare un cliente e un secondo form vengono visualizzati gli ordini del cliente selezionato. Questa procedura dettagliata viene illustrato come creare un metodo nel secondo form che riceve i dati del primo form.  
  
> [!NOTE]
>  Questa procedura dettagliata illustra solo un modo per passare dati tra i form. Sono disponibili altre opzioni per passare dati a un form, inclusa la creazione di un secondo costruttore per la ricezione di dati, o la creazione di una proprietà pubblica che può essere impostata con i dati del primo form.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di una nuova **applicazioni Windows** progetto.  
  
-   Creazione e configurazione di un set di dati con il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Selezione del controllo da creare nel form quando si trascinano elementi dal **Zdroje dat** finestra. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di un controllo con associazione a dati trascinando elementi dal **Zdroje dat** finestra in un form.  
  
-   Creazione di un secondo form con una griglia per la visualizzazione dei dati.  
  
-   Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.  
  
-   Passaggio dei dati da un form all'altro.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-the-windows-application"></a>Creare l'applicazione di Windows  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto `PassingDataBetweenForms`.  
  
3.  Selezionare **Windows Forms Application**, fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **PassingDataBetweenForms** progetto viene creato e aggiunto alla **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
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
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Per creare una griglia con associazione a dati nel form  
  
-   Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei **Form1**.  
  
     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nella **Form1**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
## <a name="create-the-second-form-form2"></a>Creare il secondo form (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Per creare un secondo form al quale passare i dati  
  
1.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.  
  
2.  Lasciare il nome predefinito **Form2**, fare clic su **Add**.  
  
3.  Trascinare l'oggetto principale **ordini** nodo dalle **Zdroje dat** finestra nei **Form2**.  
  
     Oggetto <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per l'esplorazione dei record vengono visualizzati nella **Form2**. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
4.  Eliminare il **OrdersBindingNavigator** dalla barra dei componenti.  
  
     Il **OrdersBindingNavigator** scompare dal **Form2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Aggiungere una query TableAdapter a Form2 per caricare gli ordini del cliente selezionato nel Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Per creare una query TableAdapter  
  
1.  Fare doppio clic il **NorthwindDataSet. xsd** del file in **Esplora soluzioni**.  
  
2.  Fare doppio clic il **OrdersTableAdapter**e selezionare **Aggiungi Query**.  
  
3.  Lasciare l'opzione predefinita **Usa istruzioni SQL**, quindi fare clic su **successivo**.  
  
4.  Lasciare l'opzione predefinita **SELECT che restituisce righe**, quindi fare clic su **successivo**.  
  
5.  Aggiungere una clausola WHERE alla query, per restituire `Orders` base il `CustomerID`. La query dovrebbe essere simile alla seguente:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Verificare che la sintassi dei parametri sia corretta per il database. In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.  
  
6.  Scegliere **Avanti**.  
  
7.  Per il **inserire un nome DataTableMethod**, tipo `FillByCustomerID`.  
  
8.  Cancella il **Restituisci un DataTable** opzione e quindi fare clic su **successivo**.  
  
9. Scegliere **Fine**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Creare un metodo su Form2 al quale passare i dati  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Per creare un metodo al quale passare i dati  
  
1.  Fare doppio clic su **Form2**e selezionare **Visualizza codice** per aprire **Form2** nel **Editor di codice**.  
  
2.  Aggiungere il codice seguente a **Form2** dopo il `Form2_Load` metodo:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Creare un metodo su Form1 per passare i dati e visualizzare Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Per creare un metodo per il passaggio dei dati a Form2  
  
1.  Nelle **Form1**, fare doppio clic su griglia dati del cliente e quindi fare clic su **proprietà**.  
  
2.  Nel **delle proprietà** finestra, fare clic su **eventi**.  
  
3.  Fare doppio clic il **CellDoubleClick** evento.  
  
     Verrà visualizzato l'editor del codice.  
  
4.  Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Fare doppio clic su un record del cliente nella **Form1** per aprire **Form2** con gli ordini del cliente.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).  
  
-   Aggiunta di funzionalità per il salvataggio dei dati nel database. Per altre informazioni, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)

