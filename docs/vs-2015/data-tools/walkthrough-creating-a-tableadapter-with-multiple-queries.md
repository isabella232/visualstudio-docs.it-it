---
title: 'Procedura dettagliata: Creazione di un oggetto TableAdapter con più query | Microsoft Docs'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528420"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>Procedura dettagliata: creazione di un oggetto TableAdapter con più query
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata, si creerà un TableAdapter in un set di dati usando il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). La procedura dettagliata illustra il processo di creazione di una seconda query nel [TableAdapter](../data-tools/tableadapter-overview.md) usando il [modifica TableAdapter](../data-tools/editing-tableadapters.md) all'interno di [Progettazione Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di una nuova **applicazioni Windows** progetto.  
  
-   Creare e configurare un'origine dati nell'applicazione creando un set di dati con il **configurazione guidata origine dati**.  
  
-   Aprire il nuovo set di dati nel **Progettazione Dataset**.  
  
-   Aggiunta di query al TableAdapter con la **configurazione guidata Query TableAdapter**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind nella versione SQL Server o Access. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application"></a>Creazione di una nuova applicazione Windows  
 Il primo passaggio consiste nella creazione di un'applicazione Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Per creare un nuovo progetto Applicazione Windows  
  
1.  Nelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], dal **File** menu, creare un nuovo progetto.  
  
2.  Scegliere un linguaggio di programmazione le **tipi di progetto** riquadro.  
  
3.  Fare clic su **applicazione di Windows** nel **modelli** riquadro.  
  
4.  Denominare il progetto `TableAdapterQueriesWalkthrough`, quindi fare clic su **OK**.  
  
     Visual Studio aggiunge il progetto **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>Creazione di un'origine dati di database con un TableAdapter  
 Questo passaggio viene creata un'origine dati usando il **configurazione guidata origine dati** base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.  
  
6.  Fare clic su **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.  
  
7.  Espandere la **tabelle** nodo il **Scegli oggetti di Database** pagina.  
  
8.  Selezionare il **clienti** tabella e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il **clienti** inclusa nella tabella il **Zdroje dat** finestra.  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>Apertura del set di dati in Progettazione DataSet.  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>Per aprire il set di dati in Progettazione DataSet.  
  
1.  Fare doppio clic su **NorthwindDataset** nel **Zdroje dat** finestra.  
  
2.  Nel menu di scelta rapida, scegliere **modifica il DataSet con Progettazione**.  
  
     NorthwindDataset viene aperto nel **Progettazione Dataset**.  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>Aggiunta di una seconda query a CustomersTableAdapter  
 La procedura guidata creato il set di dati con un **clienti** tabella dei dati e **CustomersTableAdapter**. In questa sezione della procedura dettagliata consente di aggiungere una seconda query per il **CustomersTableAdapter**.  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>Per aggiungere una query a CustomersTableAdapter  
  
1.  Trascinare un **Query** dal **set di dati** scheda della finestra di **della casella degli strumenti** nel **i clienti** tabella.  
  
     Il [modifica di TableAdapter](../data-tools/editing-tableadapters.md) apre.  
  
2.  Selezionare **Usa istruzioni SQL**, quindi fare clic su **successivo**.  
  
3.  Selezionare **SELECT che restituisce righe**, quindi fare clic su **successivo**.  
  
4.  Aggiungere una clausola WHERE alla query in modo da ottenere quanto segue:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Se si usa la versione Access di Northwind, sostituire il @City parametro con un punto interrogativo. (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  Nel **scegliere i metodi per generare** pagina, denominare il **Riempi un DataTable** metodo `FillByCity`.  
  
    > [!NOTE]
    >  Il metodo **Restituisci un DataTable** non viene utilizzato in questa procedura dettagliata, pertanto è possibile deselezionare la casella di controllo o lasciare il nome predefinito.  
  
6.  Fare clic su **successivo** e completare la procedura guidata.  
  
     Il **FillByCity** query viene aggiunto per il **CustomersTableAdapter**.  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>Aggiunta di codice per l'esecuzione della query aggiuntiva nel form  
  
#### <a name="to-execute-the-query"></a>Per eseguire la query  
  
1.  Selezionare **Form1** nelle **Esplora soluzioni**, fare clic su **Progettazione viste**.  
  
2.  Trascinare il **i clienti** nodo dal **Zdroje dat** finestra **Form1**.  
  
3.  Passare alla visualizzazione codice scegliendo **codice** dalle **visualizzazione** menu.  
  
4.  Sostituire il codice nel gestore eventi `Form1_Load` con il codice seguente per eseguire la query `FillByCity`.  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5.  
  
-   La griglia viene compilata con i clienti il cui valore `City` corrisponde a `Seattle`.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
### <a name="to-add-functionality-to-your-application"></a>Per aggiungere funzionalità all'applicazione  
  
-   Aggiungere un controllo <xref:System.Windows.Forms.TextBox> e un controllo <xref:System.Windows.Forms.Button> e passare il valore contenuto nella casella di testo alla query. (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   Aggiungere la logica di convalida all'evento <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati nel set di dati. Per altre informazioni, vedere [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)