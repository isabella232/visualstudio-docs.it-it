---
title: "Procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF | Microsoft Docs"
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 787be52eeb546d2ab184a172464862d10cb43288
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299578"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata verrà creata un'applicazione WPF che Visualizza i dati da tabelle di database che dispongono di una relazione padre/figlio. I dati vengono incapsulati in entità in un Entity Data Model. L'entità padre contiene informazioni generali per un set di ordini. Ogni proprietà di questa entità è associata a un controllo diverso nell'applicazione. L'entità figlio contiene i dettagli per ogni ordine. Questo set di dati è associato a un controllo <xref:System.Windows.Controls.DataGrid>.

 Questa procedura dettagliata illustra le attività seguenti:

- Creazione di un'applicazione WPF e di una Entity Data Model generata dai dati nel database di esempio AdventureWorksLT.

- Creazione di un set di controlli associati a dati che visualizzano informazioni generali per un set di ordini. Per creare i controlli, trascinare un'entità padre dalla finestra **origini dati** a **WPF Designer**.

- Creazione di un controllo <xref:System.Windows.Controls.DataGrid> che Visualizza i dettagli correlati per ogni ordine selezionato. Per creare i controlli, trascinare un'entità figlio dalla finestra **origini dati** a una finestra di **Progettazione WPF**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisiti
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato. È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](https://go.microsoft.com/fwlink/?linkid=87843).

  Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:

- Modelli di Entity Data Model e ADO.NET Entity Framework. Per ulteriori informazioni, vedere [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Uso di WPF Designer. Per ulteriori informazioni, vedere [Cenni preliminari su WPF e Silverlight Designer](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Data binding WPF. Per altre informazioni, vedere la [panoramica del data binding](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Creazione del progetto
 Creare un nuovo progetto WPF per visualizzare i record degli ordini.

#### <a name="to-create-a-new-wpf-project"></a>Per creare un nuovo progetto WPF

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Espandere **Visual C#**  o **Visual Basic**, quindi selezionare **Windows**.

4. Assicurarsi che **.NET Framework 4** sia selezionato nella casella combinata nella parte superiore della finestra di dialogo. Il controllo <xref:System.Windows.Controls.DataGrid> usato in questa procedura dettagliata è disponibile solo nella .NET Framework 4.

5. Selezionare il modello di progetto **Applicazione WPF**.

6. Nella casella **Nome** digitare `AdventureWorksOrdersViewer`.

7. fare clic su **OK**.

     Visual Studio crea il progetto `AdventureWorksOrdersViewer`.

## <a name="creating-an-entity-data-model-for-the-application"></a>Creazione di un Entity Data Model per l'applicazione
 Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**. In questa procedura dettagliata il modello di dati è un Entity Data Model.

#### <a name="to-create-an-entity-data-model"></a>Per creare un modello Entity Data Model

1. Scegliere **Aggiungi nuova origine dati** dal menu **dati** per aprire la **Configurazione guidata origine dati**.

2. Nella pagina **scegliere un tipo di origine dati** fare clic su **database**e quindi su **Avanti**.

3. Nella pagina **scegliere un modello di database** fare clic su **Entity Data Model**e quindi su **Avanti**.

4. Nella pagina **Scegli contenuto Model** fare clic su **genera da database**, quindi fare clic su **Avanti**.

5. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

   - Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.

      -oppure-

   - Fare clic su **nuova connessione** e creare una connessione al database AdventureWorksLT.

     Assicurarsi che l'opzione **Salva le impostazioni di connessione dell'entità in app. config come** sia selezionata, quindi fare clic su **Avanti**.

6. Nella pagina **Seleziona oggetti di database** espandere **tabelle**e quindi selezionare le tabelle seguenti:

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. Fare clic su **Fine**.

8. Compilazione del progetto.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Creazione di controlli associati a dati che visualizzano gli ordini
 Creare controlli che consentono di visualizzare i record degli ordini trascinando l'entità `SalesOrderHeaders` dalla finestra **origini dati** a WPF Designer.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Per creare controlli associati a dati che visualizzano i record degli ordini

1. In **Esplora soluzioni**fare doppio clic su MainWindow. XAML.

    La finestra verrà aperta in WPF Designer.

2. Modificare il codice XAML in modo che le proprietà **Height** e **Width** siano impostate su 800

3. Nella finestra **origini dati** fare clic sul menu a discesa del nodo **SalesOrderHeaders** e selezionare **Details**.

4. Espandere il nodo **SalesOrderHeaders**.

5. Fare clic sul menu a discesa accanto a **SalesOrderID** e selezionare **ComboBox**.

6. Per ognuno dei nodi figlio seguenti del nodo **SalesOrderHeaders** , fare clic sul menu a discesa accanto al nodo e selezionare **None**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **Subtotale**

   - **TaxAmt**

   - **Freight**

   - **rowguid**

   - **ModifiedDate**

     Questa azione impedisce a Visual Studio di creare i controlli associati a dati per questi nodi nel passaggio successivo. Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.

7. Dalla finestra **origini dati** trascinare il nodo **SalesOrderHeaders** nella finestra di **Progettazione WPF**.

    Visual Studio genera XAML che crea un set di controlli associati ai dati nell'entità **SalesOrderHeaders** e il codice che carica i dati. Per altre informazioni sul codice XAML e sul codice generato, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. Nella finestra di progettazione fare clic sulla casella combinata accanto all'etichetta **Sales Order ID** .

9. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Creazione di un DataGrid che Visualizza i dettagli dell'ordine
 Creare un controllo <xref:System.Windows.Controls.DataGrid> che Visualizza i dettagli dell'ordine trascinando l'entità `SalesOrderDetails` dalla finestra **origini dati** a WPF Designer.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Per creare un DataGrid che Visualizza i dettagli dell'ordine

1. Nella finestra **origini dati** individuare il nodo **SalesOrderDetails** figlio del nodo **SalesOrderHeaders** .

   > [!NOTE]
   > Esiste anche un nodo **SalesOrderDetails** che è un peer del nodo **SalesOrderHeaders** . Assicurarsi di selezionare il nodo figlio del nodo **SalesOrderHeaders** .

2. Espandere il nodo **SalesOrderDetails** figlio.

3. Per ognuno dei seguenti nodi figlio del nodo **SalesOrderDetails** , fare clic sul menu a discesa accanto al nodo e selezionare **nessuno**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **rowguid**

   - **ModifiedDate**

     Questa azione impedisce a Visual Studio di includere questi dati nel controllo <xref:System.Windows.Controls.DataGrid> creato nel passaggio successivo. Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.

4. Dalla finestra **origini dati** trascinare il nodo **SalesOrderDetails** figlio nella finestra di **Progettazione WPF**.

    Visual Studio genera XAML per definire un nuovo controllo <xref:System.Windows.Controls.DataGrid> associato a dati e il controllo viene visualizzato nella finestra di progettazione. Visual Studio aggiorna anche il metodo di `GetSalesOrderHeadersQuery` generato nel file code-behind per includere i dati nell'entità **SalesOrderDetails** .

## <a name="testing-the-application"></a>Test dell'applicazione
 Compilare ed eseguire l'applicazione per verificare che vengano visualizzati i record degli ordini.

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Premere **F5**.

     L'applicazione verrà compilata ed eseguita. Verificare quanto segue:

    - Nella casella combinata **ID ordine vendita** viene visualizzato **71774**. Si tratta dell'ID del primo ordine nell'entità.

    - Per ogni ordine selezionato nella casella combinata **Sales Order ID** , le informazioni dettagliate sugli ordini vengono visualizzate nel <xref:System.Windows.Controls.DataGrid>.

2. Chiudere l'applicazione.

## <a name="next-steps"></a>Passaggi successivi
 Al termine di questa procedura dettagliata, viene illustrato come utilizzare la finestra **origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati. Per altre informazioni, vedere [associare controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) e [associare controlli WPF a un DataSet](../data-tools/bind-wpf-controls-to-a-dataset.md).

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)