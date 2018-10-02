---
title: Creare un controllo utente Windows Form che supporta il data binding semplice | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5cb2d1e9d1ea175122381c19fa93c9abc07b2a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526539"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding semplice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creare un controllo utente che supporta il data binding semplice](https://docs.microsoft.com/visualstudio/data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding).  
  
  
Quando si visualizzano dati nei form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non è disponibile nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Form in fase di progettazione](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:  
  
|Utilizzo dell'attributo di data binding|  
|-----------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella. Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind. Il controllo utente semplice visualizzerà i numeri di telefono dei clienti in un formato telefonico standard, usando un <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazioni Windows**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `DefaultBindingProperty`.  
  
-   Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.  
  
-   Impostare il **Phone** colonna il **Zdroje dat** finestra da utilizzare il nuovo controllo.  
  
-   Creare un form per visualizzare i dati nel controllo.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  In Visual Studio, dai **File** menu, creare un nuovo **progetto**.  
  
2.  Denominare il progetto **SimpleControlWalkthrough**.  
  
3.  Selezionare **applicazione di Windows** e fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il **SimpleControlWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 Questa procedura dettagliata crea un controllo data binding semplice da un **controllo utente**, quindi l'aggiunta di un **controllo utente** elemento per il **SimpleControlWalkthrough** progetto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto  
  
1.  Dal **Project** menu, scegliere **Aggiungi controllo utente**.  
  
2.  Tipo di `PhoneNumberBox` nell'area nome, quindi fare clic su **Add**.  
  
     Il **PhoneNumberBox** controllo viene aggiunto al **Esplora soluzioni**e nella finestra di progettazione.  
  
## <a name="design-the-phonenumberbox-control"></a>Progettare il controllo PhoneNumberBox  
 Questa procedura dettagliata estende l'oggetto <xref:System.Windows.Forms.MaskedTextBox> per creare il controllo `PhoneNumberBox`.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Per progettare il controllo PhoneNumberBox  
  
1.  Trascinare un <xref:System.Windows.Forms.MaskedTextBox> dal **casella degli strumenti** nell'area di progettazione del controllo utente.  
  
2.  Selezionare lo smart tag nella <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.  
  
3.  Selezionare **numero di telefono** nel **maschera di Input** la finestra di dialogo e fare clic su **OK** per impostare la maschera.  
  
## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto  
 Per controlli semplici che supportano il data binding, implementare l'attributo <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Per implementare l'attributo DefaultBindingProperty  
  
1.  Passare al controllo `PhoneNumberBox` per la visualizzazione del codice. (Nelle **View** menu, scegliere **codice**.)  
  
2.  Sostituire il codice nel controllo `PhoneNumberBox` con la stringa seguente:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
 Questo passaggio Usa la **configurazione dell'origine dati**procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.  
  
3.  Nel **scegliere un tipo di origine dati** pagina, selezionare **Database**, quindi fare clic su **successivo**.  
  
4.  Nel **scegliere la connessione dati** pagina, effettuare una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.  
  
7.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.  
  
8.  Selezionare il `Customers` tabella e quindi fare clic su **fine**.  
  
     Il **NorthwindDataSet** viene aggiunto al progetto e il `Customers` inclusa nella tabella di **Zdroje dat** finestra.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Impostare la colonna telefono per usare il controllo PhoneNumberBox  
 All'interno di **Zdroje dat** finestra, è possibile impostare il controllo deve essere creato prima di trascinare gli elementi nel form.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Per impostare la colonna Telefono allo scopo di eseguire l'associazione al controllo PhoneNumberBox  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere la **clienti** nodo il **Zdroje dat** finestra.  
  
3.  Fare clic sulla freccia giù sul **clienti** nodo, scegliere **dettagli** dall'elenco di controllo.  
  
4.  Fare clic sulla freccia giù sul **Phone** colonna e scegliere **Personalizza**.  
  
5.  Selezionare il **PhoneNumberBox** dall'elenco dei **controlli associati** nel **opzioni di personalizzazione dell'interfaccia utente dati** nella finestra di dialogo.  
  
6.  Fare clic sulla freccia giù sul **Phone** colonna e scegliere **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al form  
 È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
-   Trascinare l'oggetto principale **i clienti** nodo dal **Zdroje dat** finestra nei form e verificare che il `PhoneNumberBox` controllo viene usato per visualizzare i dati nel `Phone` colonna.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:  
  
-   Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.  
  
-   Creazione di controlli che supportano scenari di associazioni di dati più complessi. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

