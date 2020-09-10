---
title: Creare controlli utente che supportano data binding semplici
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b1e8540a33dc5ddbead5debcbfb2cd4ddc8d9de
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742823"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding semplice

Quando si visualizzano dati nei form delle applicazioni Windows, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. I controlli che implementano <xref:System.ComponentModel.DefaultBindingPropertyAttribute> possono contenere una proprietà associabile ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.TextBox> o <xref:System.Windows.Forms.CheckBox>.

Per ulteriori informazioni sulla creazione di controlli, vedere [sviluppo di controlli Windows Forms in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo degli attributi di associazione dati|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Per ulteriori informazioni, vedere la pagina relativa alla [creazione di un Windows Forms controllo utente che supporta data binding complessi](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un Windows Forms controllo utente che supporta la ricerca data binding](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Questa procedura dettagliata crea un controllo semplice che visualizza i dati di una singola colonna in una tabella. Questo esempio usa la colonna `Phone` della tabella `Customers` del database di esempio Northwind. Il controllo utente semplice Visualizza i numeri di telefono dei clienti in un formato di numero telefonico standard, usando un <xref:System.Windows.Forms.MaskedTextBox> e impostando la maschera su un numero di telefono.

Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova **applicazione Windows Forms**.

- Aggiungere un nuovo **controllo utente** al progetto.

- Progettare visivamente il controllo utente.

- Implementare l'attributo `DefaultBindingProperty`.

- Creare un set di dati con la **Configurazione guidata origine dati** .

- Impostare la colonna **Telefono** nella finestra **Origini dati** per usare il nuovo controllo.

- Creare un form per visualizzare i dati nel controllo.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**è possibile installare SQL Server Express database locale come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel **programma di installazione di Visual Studio**. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare un' **applicazione Windows Forms**:

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Forms** .

4. Denominare il progetto **SimpleControlWalkthrough**, quindi scegliere **OK**.

     Il progetto **SimpleControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Questa procedura dettagliata crea un controllo associabile ai dati semplice da un **controllo utente**. Aggiungere un elemento di **controllo utente** al progetto **SimpleControlWalkthrough** :

1. Scegliere **Aggiungi controllo utente** dal menu **Progetto**.

2. Digitare **PhoneNumberBox** nell'area Nome, quindi scegliere **Aggiungi**.

     Il controllo **PhoneNumberBox** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.

## <a name="design-the-phonenumberbox-control"></a>Progettare il controllo PhoneNumberBox

In questa procedura dettagliata viene espansa la esistente <xref:System.Windows.Forms.MaskedTextBox> per creare il controllo **PhoneNumberBox** :

1. Trascinare un oggetto <xref:System.Windows.Forms.MaskedTextBox> dalla **Casella degli strumenti** nell'area di progettazione del controllo utente.

2. Selezionare lo smart tag sull'oggetto <xref:System.Windows.Forms.MaskedTextBox> appena trascinato e scegliere **Imposta maschera**.

3. Selezionare **Numero di telefono** nella finestra di dialogo **Maschera input** e fare clic su **OK** per impostare la maschera.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo obbligatorio di associazione dati

Per controlli semplici che supportano il data binding, implementare l'attributo <xref:System.ComponentModel.DefaultBindingPropertyAttribute>:

1. Passare il controllo **PhoneNumberBox** alla visualizzazione codice. Scegliere **Codice** dal menu **Visualizza**.

2. Sostituire il codice in **PhoneNumberBox** con quanto segue:

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. Scegliere **Compila soluzione**dal menu **Compila** .

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

In questo passaggio viene utilizzata la **Configurazione guidata origine dati** per creare un'origine dati basata sulla `Customers` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database Northwind di esempio, vedere [procedura: installare database di](../data-tools/installing-database-systems-tools-and-samples.md)esempio.

1. Per aprire la finestra **origini dati** , scegliere **Mostra origini dati**dal menu **dati** .

2. Nella finestra **origini dati** selezionare **Aggiungi nuova origine dati** per avviare la configurazione guidata **origine dati** .

3. Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.

4. Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.

7. Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

8. Selezionare la tabella `Customers`, quindi fare clic su **Fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e la `Customers` tabella viene visualizzata nella finestra **origini dati** .

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Impostare la colonna Phone per l'uso del controllo PhoneNumberBox

All'interno della finestra **origini dati** è possibile impostare il controllo da creare prima di trascinare gli elementi nel form:

1. Aprire **Form1** nella finestra di progettazione.

2. Espandere il nodo **Customers** nella finestra **Origini dati**.

3. Fare clic sulla freccia a discesa nel nodo **Customers** e scegliere **Dettagli** dall'elenco di controllo.

4. Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **Personalizza**.

5. Selezionare **PhoneNumberBox** dall'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.

6. Fare clic sulla freccia a discesa nella colonna **Telefono** e scegliere **PhoneNumberBox**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

Per creare controlli associati a dati nel form, trascinare il nodo **Customers** principale dalla finestra **origini dati** nel form e verificare che il controllo **PhoneNumberBox** sia usato per visualizzare i dati nella colonna **Phone** .

Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5** per eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

- Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

- Creazione di controlli che supportano scenari di associazioni di dati più complessi. Per altre informazioni, vedere [creare un Windows Forms controllo utente che supporta data binding complessi](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [creare un controllo utente Windows Forms che supporti data binding di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
