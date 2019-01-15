---
title: Salvare dati in un database (a più tabelle)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2a9cde551796d43cf94c20a9e54768ea9df3ddb5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924800"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare dati in un database (a più tabelle)

Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.

È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano tabelle dal **Zdroje dat** finestra in un form, il codice necessario per salvare i dati viene aggiunto automaticamente. Le tabelle aggiuntive che vengono aggiunti a un form richiedono l'aggiunta manuale di questo codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.

Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di una nuova **Windows Forms Application** progetto.

-   Creazione e configurazione di un'origine dati nell'applicazione con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

-   Impostazione dei controlli degli elementi di [finestra Origini dati](add-new-data-sources.md#data-sources-window). Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.

-   Modifica di alcuni record in ogni tabella nel set di dati.

-   Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-the-windows-forms-application"></a>Creare l'applicazione Windows Form

Il primo passaggio consiste nel creare un **Windows Forms Application**. L'assegnazione di un nome al progetto è facoltativa durante questo passaggio, ma viene assegnato un nome perché il progetto verranno salvate in un secondo momento.

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual C#**  oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Desktop di Windows**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **UpdateMultipleTablesWalkthrough**, quindi scegliere **OK**.

     Il progetto **UpdateMultipleTablesWalkthrough** viene creato e aggiunto in **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database di esempio Northwind, vedere [come: Installare i database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

1. Nel **Data** dal menu **Mostra origini dati**.

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nel **scegliere un tipo di origine dati** schermata, seleziona **Database**e quindi selezionare **Next**.

4. Nel **scegliere la connessione dati** schermata, effettuare una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **successivo**.

6. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione**, selezionare **successivo**.

7. Nel **Scegli oggetti di Database** schermata, quindi espandere il **tabelle** nodo.

8. Selezionare il **clienti** e **ordini** tabelle e quindi selezionare **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.

## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare

Per i dati in questa procedura dettagliata il `Customers` la tabella è in un **dettagli** layout in cui i dati vengono visualizzati in singoli controlli. I dati dal `Orders` tabella si trova in un **griglia** layout che viene visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati

1. Nel **Zdroje dat** finestra, espandere il **clienti** nodo.

2. Nel **clienti** nodo, seleziona **dettagli** dall'elenco di controllo per impostare il controllo della **clienti** tabella sui singoli controlli. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Creare il form con associazione a dati

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

1. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

2. Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.

    > [!NOTE]
    > Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un' `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-code-to-update-the-database"></a>Aggiungere il codice per aggiornare il database

È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**. Per impostazione predefinita, un gestore eventi per il **salvare** pulsante del<xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del modulo per inviare aggiornamenti al database. Questa procedura consente di modificare il codice per inviare gli aggiornamenti nell'ordine corretto. Ciò elimina la possibilità di generare errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.

> [!NOTE]
> Per maggiore chiarezza, questa procedura dettagliata non utilizza una transazione. Tuttavia, se si stanno aggiornando due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che assicura che tutte le modifiche relative a un database vengano completate prima che eventuali modifiche vanno eseguito il commit. Per altre informazioni, vedere [transazioni e concorrenza](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione

1. Selezionare il **salvare** pulsante la <xref:System.Windows.Forms.BindingNavigator>. Si aprirà l'Editor di codice per il `bindingNavigatorSaveItem_Click` gestore dell'evento.

2. Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> e <xref:System.Data.DataRowState.Modified>). Gli aggiornamenti vengono eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testare l'applicazione

1. Premere **F5**.

2. Apportare alcune modifiche ai dati di uno o più record di ogni tabella.

3. Selezionare il **salvare** pulsante.

4. Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)