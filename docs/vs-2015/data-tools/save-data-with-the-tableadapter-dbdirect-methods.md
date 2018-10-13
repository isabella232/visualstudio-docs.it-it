---
title: Salvare i dati con il DBDirect di TableAdapter metodi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6bb326f1cad6ea019c5d057ca24d198c28dca2a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220814"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare dati con i metodi DBDirect di TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Questa procedura dettagliata vengono fornite istruzioni dettagliate per l'esecuzione di istruzioni SQL direttamente su un database utilizzando i metodi DBDirect di un oggetto TableAdapter. I metodi DBDirect di un oggetto TableAdapter forniscono un elevato livello di controllo degli aggiornamenti del database. È possibile utilizzarli per eseguire istruzioni SQL specifiche e stored procedure chiamando i singoli `Insert`, `Update`, e `Delete` metodi secondo le esigenze dell'applicazione (a differenza di overload `Update` metodo che esegue l'aggiornamento INSERT e istruzioni di eliminazione in un'unica chiamata).  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazioni Windows**.  
  
-   Creare e configurare un set di dati con il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Selezionare il controllo da creare nel form quando si trascinano elementi dal **Zdroje dat** finestra. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creare un form con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
-   Aggiungere i metodi per accedere al database direttamente ed eseguire gli inserimenti, aggiornamenti ed eliminazioni...  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  In Visual Studio sul **File** menu, creare un nuovo **progetto**.  
  
2.  Denominare il progetto **TableAdapterDbDirectMethodsWalkthrough**.  
  
3.  Selezionare **applicazione di Windows**e thenselect**OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto al progetto **Esplora soluzioni**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
 Questo passaggio Usa la **configurazione guidata origine dati** per creare un'origine dati basata sul `Region` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Nel **Data** dal menu**Mostra origini dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.  
  
3.  Nel **scegliere un tipo di origine dati**schermata, seleziona **Database**e quindi selezionare**Next**.  
  
4.  Nel **scegliere la connessione dati**schermata, effettuare una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         oppure  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare**successivo**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione**schermata, seleziona **successivo**.  
  
7.  Nel **Scegli oggetti di Database**schermata, quindi espandere il **tabelle** nodo.  
  
8.  Selezionare il `Region` tabella e quindi selezionare**fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il `Region` inclusa nella tabella di **Zdroje dat** finestra.  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols al form per visualizzare i dati  
 Creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare dati associati a controlli nel form di Windows  
  
-   Trascinare l'oggetto principale **regione** nodo dal **Zdroje dat** finestra nei form.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter  
  
1.  Trascinare tre <xref:System.Windows.Forms.Button> dei controlli il **casella degli strumenti** nello **Form1** (sotto la **RegionDataGridView**).  
  
2.  Impostare le opzioni seguenti **Name** e **testo** le proprietà per ogni pulsante.  
  
    |nome|Testo|  
    |----------|----------|  
    |`InsertButton`|**Inserisci**|  
    |`UpdateButton`|**Aggiornamento**|  
    |`DeleteButton`|**Eliminazione**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database  
  
1.  Selezionare**InsertButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.  
  
2.  Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database  
  
1.  Fare doppio clic il **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.  
  
2.  Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere il codice per eliminare record dal database  
  
1.  Selezionare**DeleteButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.  
  
2.  Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Selezionare**F5** per eseguire l'applicazione.  
  
-   Selezionare il **Inserisci** pulsante e verificare che il nuovo record venga visualizzato nella griglia.  
  
-   Selezionare il **Update** pulsante e verificare che il record viene aggiornato nella griglia.  
  
-   Selezionare il **eliminare** pulsante e verificare che il record viene rimosso dalla griglia.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, sono disponibili diversi passaggi, che si potrebbe voler eseguire dopo la creazione di un form con associazione a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form. Per altre informazioni, vedere [procedura: aggiungere una Query con parametri a un'applicazione di Windows Forms](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Aggiunta di altre tabelle al set di dati selezionando **configura il DataSet con Creazione guidata** dall'interno di **Zdroje dat** finestra. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form. Per altre informazioni, vedere [Procedura: Visualizzare dati correlati in un'applicazione Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)

