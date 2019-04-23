---
title: Creare un controllo utente Windows Form che supporta il data binding semplice | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: edec23d840723e37ecb469aadc412e5659e95007
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071018"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding semplice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si visualizzano dati nei form delle applicazioni Windows, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Form in fase di progettazione](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:  
  
|Utilizzo dell'attributo di data binding|  
|-----------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|  
  
 Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella. Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind. Il controllo utente semplice visualizzerà i numeri di telefono dei clienti in un formato telefonico standard, usando un <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
- Creare una nuova **applicazioni Windows**.  
  
- Aggiungere un nuovo **controllo utente** al progetto.  
  
- Progettare visivamente il controllo utente.  
  
- Implementare l'attributo `DefaultBindingProperty`.  
  
- Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.  
  
- Impostare la colonna **Telefono** nella finestra **Origini dati** per usare il nuovo controllo.  
  
- Creare un form per visualizzare i dati nel controllo.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
- Accedere al database di esempio Northwind.
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1. In Visual Studio, dai **File** menu, creare un nuovo **progetto**.  
  
2. Denominare il progetto **SimpleControlWalkthrough**.  
  
3. Selezionare **applicazione di Windows** e fare clic su **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il progetto **SimpleControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 Questa procedura dettagliata crea un controllo data binding semplice da un **controllo utente**, quindi l'aggiunta di un **controllo utente** elemento per il **SimpleControlWalkthrough** progetto.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto  
  
1. Scegliere **Aggiungi controllo utente** dal menu **Progetto**.  
  
2. Tipo di `PhoneNumberBox` nell'area nome, quindi fare clic su **Add**.  
  
     Il controllo **PhoneNumberBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.  
  
## <a name="design-the-phonenumberbox-control"></a>Progettare il controllo PhoneNumberBox  
 Questa procedura dettagliata espande l'oggetto <xref:System.Windows.Forms.MaskedTextBox> per creare il controllo `PhoneNumberBox`.  
  
#### <a name="to-design-the-phonenumberbox-control"></a>Per progettare il controllo PhoneNumberBox  
  
1. Trascinare un oggetto <xref:System.Windows.Forms.MaskedTextBox> dalla **Casella degli strumenti** nell'area di progettazione del controllo utente.  
  
2. Selezionare lo smart tag sull'oggetto <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.  
  
3. Selezionare **Numero di telefono** nella finestra di dialogo **Maschera input** e fare clic su **OK** per impostare la maschera.  
  
## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto  
 Per controlli semplici che supportano il data binding, implementare l'attributo <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.  
  
#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Per implementare l'attributo DefaultBindingProperty  
  
1. Passare al controllo `PhoneNumberBox` per la visualizzazione del codice. Scegliere **Codice** dal menu **Visualizza**.  
  
2. Sostituire il codice nel controllo `PhoneNumberBox` con la stringa seguente:  
  
     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]  
  
3. Scegliere **Compila soluzione** dal menu **Compila**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
 Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Customers` contenuta nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind.
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1. Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3. Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.  
  
4. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.  
  
5. Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.  
  
6. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.  
  
7. Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.  
  
8. Selezionare la tabella `Customers`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Customers` viene visualizzata nella finestra **Origini dati**.  
  
## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Impostare la colonna telefono per usare il controllo PhoneNumberBox  
 Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel modulo.  
  
#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Per impostare la colonna Telefono allo scopo di eseguire l'associazione al controllo PhoneNumberBox  
  
1. Aprire **Form1** nella finestra di progettazione.  
  
2. Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
3. Fare clic sulla freccia a discesa nel nodo **Customers** e scegliere **Dettagli** dall'elenco di controllo.  
  
4. Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **Personalizza**.  
  
5. Selezionare **PhoneNumberBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.  
  
6. Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **PhoneNumberBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
- Trascinare l'oggetto principale **i clienti** nodo dal **Zdroje dat** finestra nei form e verificare che il `PhoneNumberBox` controllo viene usato per visualizzare i dati nel `Phone` colonna.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
- Premere F5 per eseguire l'applicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:  
  
- Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.  
  
- Creazione di controlli che supportano scenari di associazioni di dati più complessi. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
