---
title: Creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca | Microsoft Docs
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
- data binding, user controls
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7c0514d29d3c8e87b277115f8e1307dc0a5fb0c4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662712"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si visualizzano dati nei Windows Form, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.LookupBindingPropertiesAttribute> possono contenere tre proprietà associabili ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.ComboBox>.  
  
 Per altre informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Form in fase di progettazione](http://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).  
  
 Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:  
  
|Utilizzo dell'attributo di data binding|  
|-----------------------------------|  
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|  
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|  
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Il processo è descritto in questa pagina di procedura dettagliata.|  
  
 Questa procedura dettagliata crea un controllo di ricerca che effettua l'associazione ai dati di due tabelle. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind. Il controllo di ricerca verrà associato al campo `CustomerID` dalla tabella `Orders`. Userà questo valore per eseguire la ricerca di `CompanyName` dalla tabella `Customers`.  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazioni Windows**.  
  
-   Aggiungere un nuovo **controllo utente** al progetto.  
  
-   Progettare visivamente il controllo utente.  
  
-   Implementare l'attributo `LookupBindingProperty`.  
  
-   Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.  
  
-   Impostare la colonna **CustomerID** nella tabella **Orders** della finestra **Origini dati** per usare il nuovo controllo.  
  
-   Creare un form per visualizzare i dati nel controllo.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  In Visual Studio, dai **File** menu, creare un nuovo **progetto**.  
  
2.  Denominare il progetto **LookupControlWalkthrough**.  
  
3.  Selezionare **Windows Forms Application**, fare clic su **OK**.  
  
     Il progetto **LookupControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto  
 Dal momento che questa procedura dettagliata crea un controllo di ricerca da un **Controllo utente**, è necessario aggiungere un elemento **Controllo utente** al progetto **LookupControlWalkthrough**.  
  
#### <a name="to-add-a-user-control-to-the-project"></a>Per aggiungere un controllo utente al progetto  
  
1.  Selezionare **Aggiungi controllo utente** dal menu **Progetto**.  
  
2.  Tipo `LookupBox` nella **Name** area e quindi fare clic su **Add**.  
  
     Il controllo **LookupBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.  
  
## <a name="design-the-lookupbox-control"></a>Progettare il controllo LookupBox  
  
#### <a name="to-design-the-lookupbox-control"></a>Per progettare il controllo LookupBox  
  
-   Trascinare un oggetto <xref:System.Windows.Forms.ComboBox> dalla **Casella degli strumenti** nell'area di progettazione del controllo utente.  
  
## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto  
 Per controlli di ricerca che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.  
  
#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Per implementare l'attributo LookupBindingProperties  
  
1.  Passare al controllo **LookupBox** per la visualizzazione del codice. Scegliere **Codice** dal menu **Visualizza**.  
  
2.  Sostituire il codice nel controllo `LookupBox` con la stringa seguente:  
  
     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]  
  
3.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database  
 Questo passaggio crea un'origine dati usando la **Configurazione guidata origine dati** basata sulle tabelle `Customers` e `Orders` nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [i database di esempio di installazione di SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.  
  
7.  Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare le tabelle `Customers` e `Orders`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.  
  
## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Impostare la colonna CustomerID della tabella Orders per usare il controllo LookupBox  
 Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel modulo.  
  
#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Per impostare la colonna CustomerID da associare al controllo LookupBox  
  
1.  Aprire **Form1** nella finestra di progettazione.  
  
2.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
3.  Espandere il nodo **Orders** (nel nodo **Customers** sotto la colonna **Fax**).  
  
4.  Fare clic sulla freccia a discesa nel nodo **Orders** e scegliere **Dettagli** dall'elenco di controllo.  
  
5.  Fare clic sulla freccia a discesa nella colonna **CustomerID** (nel nodo **Orders**) e scegliere **Personalizza**.  
  
6.  Selezionare **LookupBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.  
  
7.  Fare clic su **OK**.  
  
8.  Fare clic sulla freccia a discesa nella colonna **CustomerID** e scegliere **LookupBox**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al form  
 È possibile creare i controlli associati ai dati trascinando elementi dalla finestra **Origini dati** in **Form1**.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare controlli associati ai dati nel Windows Form  
  
-   Trascinare il **ordini** nodo dalle **Zdroje dat** finestra nei Form, Windows e verificare che il **LookupBox** controllo viene usato per visualizzare i dati nel `CustomerID` colonna.  
  
## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associare il controllo di ricerca di CompanyName dalla tabella Customers  
  
#### <a name="to-setup-the-lookup-bindings"></a>Per impostare le associazioni di ricerca  
  
-   Selezionare principale **i clienti** nodo il **Zdroje dat** finestra e quindi trascinare casella combinata il **CustomerIDLookupBox** nel **Form1** .  
  
     Viene in questo modo impostato il data binding per visualizzare `CompanyName` dalla tabella `Customers`, mantenendo al contempo il valore `CustomerID` della tabella `Orders`.  
  
## <a name="running-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Spostarsi all'interno di alcuni record e verificare che `CompanyName` venga mostrato nel controllo `LookupBox`.  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
