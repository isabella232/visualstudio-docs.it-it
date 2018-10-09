---
title: Creare un controllo utente Windows Form che supporta data binding complesso | Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 27f8a0e7fca0f14ee784eddaeb30f4d734994dc9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529569"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creare un controllo utente Windows Form che supporta data binding complesso
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creare un controllo utente Windows Form con il data binding](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding).  
  
  
Quando si visualizzano dati nei form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non è disponibile nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contengono `DataSource` e la proprietà `DataMember` che può essere associata ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Form in fase di progettazione](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Quando si creano controlli da usare negli scenari di data binding è necessario implementare uno degli attributi di data binding seguenti:  
  
|Utilizzo dell'attributo di data binding|  
|-----------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Questa procedura dettagliata crea un controllo complesso che visualizza righe di dati da una tabella. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind. Il controllo utente complesso visualizzerà la tabella dei clienti in un oggetto <xref:System.Windows.Forms.DataGridView> nel controllo personalizzato.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazioni Windows**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `ComplexBindingProperty`.  
  
-   Creare un set di dati con il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Impostare il **clienti** nella tabella di [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) per usare il nuovo controllo complesso.  
  
-   Aggiungere il nuovo controllo trascinandolo dal **finestra Origini dati** nello **Form1**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  In Visual Studio, dai **File** menu, creare un nuovo **progetto**.  
  
2.  Denominare il progetto **ComplexControlWalkthrough**.  
  
3.  Selezionare **applicazione di Windows**, fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **ComplexControlWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 Poiché questa procedura dettagliata crea un controllo data binding complesso da un **controllo utente**, è necessario aggiungere un **controllo utente** elemento al progetto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto  
  
1.  Dal **Project** menu, scegliere **Aggiungi controllo utente**.  
  
2.  Tipo di **ComplexDataGridView** nel **Name** area e quindi fare clic su **Add**.  
  
     Il **ComplexDataGridView** controllo viene aggiunto al **Esplora soluzioni**e nella finestra di progettazione.  
  
## <a name="design-the-complexdatagridview-control"></a>Progettare il controllo ComplexDataGridView  
 Questo passaggio aggiunge un oggetto <xref:System.Windows.Forms.DataGridView> al controllo utente.  
  
#### <a name="to-design-the-complexdatagridview-control"></a>Per progettare il controllo ComplexDataGridView  
  
-   Trascinare un <xref:System.Windows.Forms.DataGridView> dal **casella degli strumenti** nell'area di progettazione del controllo utente.  
  
## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto  
 Per controlli semplici che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Per implementare l'attributo ComplexBindingProperties  
  
1.  Passare il **ComplexDataGridView** controllo alla visualizzazione codice. (Nelle **View** dal menu **codice**.)  
  
2.  Sostituire il codice nel controllo `ComplexDataGridView` con la stringa seguente:  
  
     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## <a name="creating-a-data-source-from-your-database"></a>Creazione di un'origine dati dal database  
 Questo passaggio Usa la **configurazione dell'origine dati** procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [i database di esempio di installazione di SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.  
  
7.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.  
  
8.  Selezionare il `Customers` tabella e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il `Customers` inclusa nella tabella di **Zdroje dat** finestra.  
  
## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Impostare la tabella Customers per usare il controllo ComplexDataGridView  
 All'interno di **Zdroje dat** finestra, è possibile impostare il controllo deve essere creato prima di trascinare gli elementi nel form.  
  
#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Per impostare la tabella Customers allo scopo di associare il controllo ComplexDataGridView  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere la **clienti** nodo il **Zdroje dat** finestra.  
  
3.  Fare clic sulla freccia giù sul **clienti** nodo, scegliere **Personalizza**.  
  
4.  Selezionare il **ComplexDataGridView** dall'elenco dei **controlli associati** nel **opzioni di personalizzazione dell'interfaccia utente dati** nella finestra di dialogo.  
  
5.  Fare clic sulla freccia giù sul `Customers` tabella e scegliere **ComplexDataGridView** dall'elenco di controllo.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al form  
 È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
-   Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei form. Verificare che il **ComplexDataGridView** controllo utilizzato per visualizzare i dati della tabella.  
  
## <a name="running-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:  
  
-   Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.  
  
-   Creazione di controlli che supportano scenari di ricerca. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Controlli Windows Form](http://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
