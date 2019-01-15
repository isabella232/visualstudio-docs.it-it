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
ms.workload:
- data-storage
ms.openlocfilehash: e310470afe6448eb328b0981236a1f41efe741f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829498"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Creare un controllo utente Windows Form che supporta il data binding complesso

Quando si visualizzano dati nei form delle applicazioni Windows, è possibile scegliere i controlli esistenti dalla **Casella degli strumenti** o creare controlli personalizzati se l'applicazione richiede funzionalità che non sono disponibili nei controlli standard. In questa procedura dettagliata è illustrato come creare un controllo che implementa <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. I controlli che implementano <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contengono `DataSource` e la proprietà `DataMember` che può essere associata ai dati. Tali controlli sono simili a <xref:System.Windows.Forms.DataGridView> o <xref:System.Windows.Forms.ListBox>.

Per altre informazioni sulla creazione di controlli, vedere [lo sviluppo di Windows Form controlli in fase di progettazione](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time).

Quando si creano controlli da usare negli scenari di data binding, è necessario implementare uno degli attributi di data binding seguenti:

|Utilizzo dell'attributo di data binding|
| - |
|Implementare <xref:System.ComponentModel.DefaultBindingPropertyAttribute> su controlli semplici, ad esempio <xref:System.Windows.Forms.TextBox>, che visualizzano una singola colonna, o proprietà, di dati. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta il data binding semplice](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implementare <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.DataGridView>, che visualizzano elenchi, o tabelle, di dati. Il processo è descritto in questa pagina di procedura dettagliata.|
|Implementare <xref:System.ComponentModel.LookupBindingPropertiesAttribute> su controlli, ad esempio <xref:System.Windows.Forms.ComboBox>, che visualizzano elenchi, o tabelle, di dati ma che devono anche presentare una singola colonna o proprietà. Per altre informazioni, vedere [creare un controllo utente Windows Form che supporta l'associazione di dati di ricerca](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

Questa procedura dettagliata crea un controllo complesso che visualizza righe di dati da una tabella. In questo esempio viene usata la tabella `Customers` del database di esempio Northwind. Il controllo utente complesso visualizzerà la tabella dei clienti in un oggetto <xref:System.Windows.Forms.DataGridView> nel controllo personalizzato.

Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova applicazione **Windows Forms Application**.

- Aggiungere un nuovo **controllo utente** al progetto.

- Progettare visivamente il controllo utente.

- Implementare l'attributo `ComplexBindingProperty`.

- Creare un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostare il **i clienti** nella tabella di [finestra Origini dati](add-new-data-sources.md#data-sources-window) per usare il nuovo controllo complesso.

- Aggiungere il nuovo controllo trascinandolo dalla finestra **Origini dati** in **Form1**.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

1. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    1. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    1. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare un **Windows Forms Application**:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

1. Espandere la **Visual C#**  oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Desktop di Windows**.

1. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

1. Denominare il progetto **ComplexControlWalkthrough**, quindi scegliere **OK**.

    Il progetto **ComplexControlWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-user-control-to-the-project"></a>Aggiungere un controllo utente al progetto

Poiché questa procedura dettagliata crea un controllo data binding complesso da un **controllo utente**, aggiungere un **controllo utente** elemento al progetto:

1. Scegliere **Aggiungi controllo utente** dal menu **Progetto**.

1. Digitare **ComplexDataGridView** nell'area **Nome** e quindi fare clic su **Aggiungi**.

    Il controllo **ComplexDataGridView** viene aggiunto a **Esplora soluzioni** e si apre nella finestra di progettazione.

## <a name="design-the-complexdatagridview-control"></a>Progettare il controllo ComplexDataGridView

Per aggiungere un <xref:System.Windows.Forms.DataGridView> al controllo utente, trascinare un <xref:System.Windows.Forms.DataGridView> dalle **della casella degli strumenti** nell'area di progettazione del controllo utente.

## <a name="add-the-required-data-binding-attribute"></a>Aggiungere l'attributo di data binding richiesto

Per controlli semplici che supportano il data binding, è possibile implementare l'attributo <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>:

1. Passare al controllo **ComplexDataGridView** per la visualizzazione del codice. Scegliere **Codice** dal menu **Visualizza**.

1. Sostituire il codice nel controllo `ComplexDataGridView` con la stringa seguente:

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Usare la **configurazione dell'origine dati** procedura guidata per creare un'origine dati in base il `Customers` tabella nel database di esempio Northwind:

1.  Per aprire la **Zdroje dat** finestra via il **Data** dal menu fare clic su **Mostra origini dati**.

2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

7.  Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.

8.  Selezionare la tabella `Customers`, quindi fare clic su **Fine**.

    L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Customers` viene visualizzata nella finestra **Origini dati**.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Impostare la tabella Customers per usare il controllo ComplexDataGridView

Nella finestra **Origini dati** è possibile impostare il controllo da creare prima di trascinare elementi nel form:

1. Aprire **Form1** nella finestra di progettazione.

1. Espandere il nodo **Customers** nella finestra **Origini dati**.

1. Fare clic sulla freccia a discesa nel nodo **Customers** e scegliere **Personalizza**.

1. Selezionare **ComplexDataGridView** nell'elenco **Controlli associati** nella finestra di dialogo **Personalizzazione dell'interfaccia utente dati**.

1. Fare clic sulla freccia a discesa nella tabella `Customers` e scegliere **ComplexDataGridView** nell'elenco di controllo.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** al form. Verificare che il **ComplexDataGridView** controllo utilizzato per visualizzare i dati della tabella.

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