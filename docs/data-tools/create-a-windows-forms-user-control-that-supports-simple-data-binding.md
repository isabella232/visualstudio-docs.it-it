---
title: Creare un controllo utente che supporta il data binding semplice
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f5bffba1b2de64c142dd70990fb74429ad40269a
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220095"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding semplice

Quando si visualizzano dati nei form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non è disponibile nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.

Per altre informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Form in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo dell'attributo di data binding|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella. Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind. Il controllo utente semplice consente di visualizzare i numeri di telefono dei clienti in un formato telefonico standard, usando un <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.

Durante questa procedura dettagliata, si apprenderà come:

-   Creare una nuova **Windows Forms Application**.

-   Aggiungere un nuovo **controllo utente** al progetto.

-   Progettare visivamente il controllo utente.

-   Implementare l'attributo `DefaultBindingProperty`.

-   Creare un set di dati con il **configurazione dell'origine dati** procedura guidata.

-   Impostare il **Phone** colonna il **Zdroje dat** finestra da utilizzare il nuovo controllo.

-   Creare un form per visualizzare i dati nel controllo.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte del **elaborazione ed archiviazione dati** carico di lavoro nel **programma di installazione di Visual Studio**.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione di Windows Form

Il primo passaggio consiste nel creare un **Windows Forms Application**:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **SimpleControlWalkthrough**, quindi scegliere **OK**.

     Il **SimpleControlWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Questa procedura dettagliata crea un controllo data binding semplice da un **controllo utente**. Aggiungere un **UserControl** voce al **SimpleControlWalkthrough** progetto:

1.  Dal **Project** menu, scegliere **Aggiungi controllo utente**.

2.  Tipo di **PhoneNumberBox** nell'area nome, quindi fare clic su **Add**.

     Il **PhoneNumberBox** controllo viene aggiunto al **Esplora soluzioni**e nella finestra di progettazione.

## <a name="design-the-phonenumberbox-control"></a>Progettare il controllo PhoneNumberBox

Questa procedura dettagliata espande l'oggetto esistente <xref:System.Windows.Forms.MaskedTextBox> per creare le **PhoneNumberBox** controllo:

1.  Trascinare un <xref:System.Windows.Forms.MaskedTextBox> dal **casella degli strumenti** nell'area di progettazione del controllo utente.

2.  Selezionare lo smart tag nella <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.

3.  Selezionare **numero di telefono** nel **maschera di Input** la finestra di dialogo e fare clic su **OK** per impostare la maschera.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto

Per controlli semplici che supportano il Data Binding, implementare il <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1.  Passare il **PhoneNumberBox** controllo alla visualizzazione codice. (Nelle **View** menu, scegliere **codice**.)

2.  Sostituire il codice nel **PhoneNumberBox** con quanto segue:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Questo passaggio Usa la **configurazione dell'origine dati** procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

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

All'interno di **Zdroje dat** finestra, è possibile impostare il controllo deve essere creato prima di trascinare gli elementi nel form:

1.  Aprire **Form1** nella finestra di progettazione.

2.  Espandere la **clienti** nodo il **Zdroje dat** finestra.

3.  Fare clic sulla freccia giù sul **clienti** nodo, scegliere **dettagli** dall'elenco di controllo.

4.  Fare clic sulla freccia giù sul **Phone** colonna e scegliere **Personalizza**.

5.  Selezionare il **PhoneNumberBox** dall'elenco dei **controlli associati** nel **opzioni di personalizzazione dell'interfaccia utente dati** nella finestra di dialogo.

6.  Fare clic sulla freccia giù sul **Phone** colonna e scegliere **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.

Per creare controlli associati a dati nel form, trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei form e verificare che il **PhoneNumberBox** controllo è Consente di visualizzare i dati di **Phone** colonna.

     Data-bound controls with descriptive labels appear on the form, along with a tool strip (<xref:System.Windows.Forms.BindingNavigator>) for navigating records. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, and <xref:System.Windows.Forms.BindingNavigator> appear in the component tray.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

Premere **F5** per eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

-   Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

-   Creazione di controlli che supportano scenari di associazioni di dati più complessi. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta data binding complesso](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)