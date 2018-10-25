---
title: Creare un controllo utente Windows Form con il data binding
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: db8059cf34c2de9a52cda18dd09ce6040bf8d841
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937902"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creare un controllo utente Windows Form che supporta data binding complesso

Quando si visualizzano dati nei form in applicazioni di Windows, è possibile scegliere i controlli esistenti dal **casella degli strumenti**, oppure è possibile creare controlli personalizzati se l'applicazione richiede funzionalità che non è disponibile nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contengono `DataSource` e la proprietà `DataMember` che può essere associata ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Per altre informazioni sulla creazione di controlli, vedere [lo sviluppo di Windows Form controlli in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare negli scenari di data binding è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo dell'attributo di data binding|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Questa procedura dettagliata crea un controllo complesso che visualizza righe di dati da una tabella. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind. Il controllo utente complesso visualizzerà la tabella dei clienti in un oggetto <xref:System.Windows.Forms.DataGridView> nel controllo personalizzato.

Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova **Windows Forms Application**.

- Aggiungere un nuovo **controllo utente** al progetto.

- Progettare visivamente il controllo utente.

- Implementare l'attributo `ComplexBindingProperty`.

- Creare un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostare il **clienti** nella tabella di [finestra Origini dati](add-new-data-sources.md) per usare il nuovo controllo complesso.

- Aggiungere il nuovo controllo trascinandolo dal **finestra Origini dati** nello **Form1**.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

1. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    1. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    1. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form

Il primo passaggio consiste nel creare un **Windows Forms Application**:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

1. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

1. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

1. Denominare il progetto **ComplexControlWalkthrough**, quindi scegliere **OK**.

    Il **ComplexControlWalkthrough** progetto viene creato e aggiunto alla **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Poiché questa procedura dettagliata crea un controllo data binding complesso da un **controllo utente**, aggiungere un **controllo utente** elemento al progetto:

1. Dal **Project** menu, scegliere **Aggiungi controllo utente**.

1. Tipo di **ComplexDataGridView** nel **Name** area e quindi fare clic su **Add**.

    Il **ComplexDataGridView** controllo viene aggiunto al **Esplora soluzioni**e nella finestra di progettazione.

## <a name="design-the-complexdatagridview-control"></a>Progettare il controllo ComplexDataGridView

Per aggiungere un <xref:System.Windows.Forms.DataGridView> al controllo utente, trascinare un <xref:System.Windows.Forms.DataGridView> dalle **della casella degli strumenti** nell'area di progettazione del controllo utente.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto

Per controlli semplici che supportano il data binding, è possibile implementare il <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Passare il **ComplexDataGridView** controllo alla visualizzazione codice. (Nelle **View** dal menu **codice**.)

1. Sostituire il codice nel controllo `ComplexDataGridView` con la stringa seguente:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Usare la **configurazione dell'origine dati** procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind:

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

7.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.

8.  Selezionare il `Customers` tabella e quindi fare clic su **fine**.

    Il **NorthwindDataSet** viene aggiunto al progetto e il `Customers` inclusa nella tabella di **Zdroje dat** finestra.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Impostare la tabella Customers per usare il controllo ComplexDataGridView

All'interno di **Zdroje dat** finestra, è possibile impostare il controllo deve essere creato prima di trascinare gli elementi nel form:

1. Aprire **Form1** nella finestra di progettazione.

1. Espandere la **clienti** nodo il **Zdroje dat** finestra.

1. Fare clic sulla freccia giù sul **clienti** nodo, scegliere **Personalizza**.

1. Selezionare il **ComplexDataGridView** dall'elenco dei **controlli associati** nel **opzioni di personalizzazione dell'interfaccia utente dati** nella finestra di dialogo.

1. Fare clic sulla freccia giù sul `Customers` tabella e scegliere **ComplexDataGridView** dall'elenco di controllo.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form. Trascinare l'oggetto principale **clienti** nodo dalle **Zdroje dat** finestra nei form. Verificare che il **ComplexDataGridView** controllo utilizzato per visualizzare i dati della tabella.

## <a name="run-the-application"></a>Esecuzione dell'applicazione

Premere **F5** per eseguire l'applicazione.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, dopo la creazione di un controllo che supporta il data binding sarà possibile eseguire diverse operazioni. Ecco alcuni dei passaggi più comuni:

- Posizionamento dei controlli personalizzati in una libreria di controlli in modo da poterli usare di nuovo in altre applicazioni.

- Creazione di controlli che supportano scenari di ricerca. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Controlli Windows Form](/dotnet/framework/winforms/controls/index)