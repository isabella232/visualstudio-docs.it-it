---
title: Salvare dati in un database (a più tabelle)
description: In questa procedura dettagliata, salvare i dati da più tabelle in un database usando gli strumenti di DataSet in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 772a4001ad999ce4c585eeac5bf5ea9b3ba97ab1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067023"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare dati in un database (a più tabelle)

Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.

È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano tabelle dalla **finestra Origini** dati in un form, viene aggiunto automaticamente il codice necessario per salvare i dati. Tutte le tabelle aggiuntive aggiunte a un modulo richiedono l'aggiunta manuale di questo codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.

Le attività illustrate nella procedura dettagliata sono le seguenti:

- Creazione e configurazione di un'origine dati nell'applicazione con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostazione dei controlli degli elementi nella [finestra Origini dati](add-new-data-sources.md#data-sources-window). Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Modifica di alcuni record in ogni tabella del set di dati.

- Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina di [download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** Nel **Programma di installazione di Visual Studio**, è possibile installare SQL Server Express Local DB come parte  del carico di lavoro Archiviazione ed elaborazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la **finestra** SQL Server Esplora oggetti. (SQL Server Esplora oggetti viene installato come parte  del carico di lavoro Archiviazione ed elaborazione dati nel Programma di installazione di Visual Studio. Espandere il **nodo SQL Server.** Fare clic con il pulsante destro del mouse Local DB'istanza di query e **scegliere Nuova query**.

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query viene completata e viene creato il database Northwind.

## <a name="create-the-windows-forms-application"></a>Creare l'Windows Forms

Creare un nuovo **progetto Windows'app Forms** per C# o Visual Basic. Assegnare al progetto il nome **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Creare l'origine dati

Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database di esempio Northwind, vedere [Procedura: Installare database di esempio.](../data-tools/installing-database-systems-tools-and-samples.md)

1. Scegliere **Mostra** origini **dati dal** menu Dati .

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **Scegliere un tipo di origine dati** selezionare **Database** e quindi **Selezionare Avanti.**

4. Nella schermata **Scegliere la connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **Avanti.**

6. In **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti.**

7. Nella schermata **Scegliere gli oggetti di database** espandere il **nodo** Tabelle.

8. Selezionare le **tabelle Customers** **e Orders** e quindi selezionare **Fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.

## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare

Per questa procedura dettagliata, i dati nella tabella si trova in un layout Dettagli in cui `Customers` i dati vengono visualizzati in singoli controlli.  I dati della tabella si trova in un layout Grid `Orders` visualizzato in un controllo  <xref:System.Windows.Forms.DataGridView> .

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati

1. Nella finestra **Origini dati** espandere il **nodo** Customers.

2. Nel nodo **Customers** selezionare **Dettagli dall'elenco** dei controlli per modificare il controllo della **tabella Customers** in singoli controlli. Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Creare il form associato a dati

È possibile creare i controlli associati a dati trascinando gli elementi dalla **finestra Origini** dati nel form.

1. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , e vengono visualizzati nella barra dei <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> componenti.

2. Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.

    > [!NOTE]
    > Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. E `OrdersTableAdapter` <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-code-to-update-the-database"></a>Aggiungere codice per aggiornare il database

È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**. Per impostazione predefinita, un gestore eventi per il **pulsante** Salva di viene aggiunto al codice del modulo per <xref:System.Windows.Forms.BindingNavigator> inviare aggiornamenti al database. Questa procedura modifica il codice per inviare gli aggiornamenti nell'ordine corretto. In questo modo si elimina la possibilità di generare errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.

> [!NOTE]
> Per maggiore chiarezza, in questa procedura dettagliata non viene utilizzata una transazione. Tuttavia, se si aggiornano due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che assicura che tutte le modifiche correlate a un database siano state apportate correttamente prima del commit delle modifiche. Per altre informazioni, vedere [Transazioni e concorrenza](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione

1. Selezionare il **pulsante** Salva in <xref:System.Windows.Forms.BindingNavigator> . Verrà aperto l'editor di codice per il `bindingNavigatorSaveItem_Click` gestore eventi.

2. Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> e <xref:System.Data.DataRowState.Modified>). Gli aggiornamenti vengono eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs" id="Snippet10":::

## <a name="test-the-application"></a>Testare l'applicazione

1. Premere **F5**.

2. Apportare alcune modifiche ai dati di uno o più record di ogni tabella.

3. Fare clic sul pulsante **Salva**.

4. Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
