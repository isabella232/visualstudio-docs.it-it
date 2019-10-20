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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bcb551cdcd5b2505c6ac536a440fcc3e70464bfb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648204"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare dati in un database (a più tabelle)

Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.

È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano le tabelle dalla finestra **origini dati** in un form, il codice necessario per salvare i dati viene aggiunto automaticamente. Qualsiasi tabella aggiuntiva aggiunta a un modulo richiede l'aggiunta manuale di questo codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.

Le attività illustrate nella procedura dettagliata sono le seguenti:

- Creazione e configurazione di un'origine dati nell'applicazione con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Impostazione dei controlli degli elementi nella [finestra Origini dati](add-new-data-sources.md#data-sources-window). Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Modifica di alcuni record in ogni tabella del set di dati.

- Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.

## <a name="prerequisites"></a>Prerequisites

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**è possibile installare SQL Server Express database locale come parte del carico di lavoro di **elaborazione e archiviazione dei dati** oppure come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-the-windows-forms-application"></a>Creare il Windows Forms Application

Creare un nuovo progetto di **App Windows Forms** per C# o Visual Basic. Assegnare al progetto il nome **UpdateMultipleTablesWalkthrough**.

## <a name="create-the-data-source"></a>Creare l'origine dati

Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database Northwind di esempio, vedere [procedura: installare database di](../data-tools/installing-database-systems-tools-and-samples.md)esempio.

1. Scegliere **Mostra origini dati**dal menu **dati** .

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati** selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         oppure

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione**selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database** espandere il nodo **tabelle** .

8. Selezionare le tabelle **Customers** e **Orders** e quindi fare clic su **Finish**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.

## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare

Per questa procedura dettagliata, i dati nella tabella `Customers` si trova in un layout **Dettagli** in cui i dati vengono visualizzati nei singoli controlli. I dati della tabella `Orders` si trova in un layout di **griglia** visualizzato in un controllo <xref:System.Windows.Forms.DataGridView>.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati

1. Nella finestra **origini dati** espandere il nodo **Customers** .

2. Nel nodo **Customers** selezionare **Details** dall'elenco di controllo per modificare il controllo della tabella **Customers** in singoli controlli. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Creare il form con associazione a dati

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

1. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

2. Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.

    > [!NOTE]
    > Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti viene visualizzata una `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource>.

## <a name="add-code-to-update-the-database"></a>Aggiungere il codice per aggiornare il database

È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**. Per impostazione predefinita, un gestore eventi per il pulsante **Salva** del <xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del form per inviare gli aggiornamenti al database. Questa procedura modifica il codice per inviare gli aggiornamenti nell'ordine corretto. In questo modo si elimina la possibilità di generare errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.

> [!NOTE]
> Per maggiore chiarezza, in questa procedura dettagliata non viene utilizzata alcuna transazione. Tuttavia, se si stanno aggiornando due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che garantisce che tutte le modifiche correlate a un database abbiano esito positivo prima del commit delle modifiche. Per ulteriori informazioni, vedere [transazioni e concorrenza](/dotnet/framework/data/adonet/transactions-and-concurrency).

### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione

1. Selezionare il pulsante **Salva** nella <xref:System.Windows.Forms.BindingNavigator>. Verrà aperto l'editor di codice per il gestore dell'evento `bindingNavigatorSaveItem_Click`.

2. Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> e <xref:System.Data.DataRowState.Modified>). Gli aggiornamenti vengono eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>Testare l'applicazione

1. Premere **F5**.

2. Apportare alcune modifiche ai dati di uno o più record di ogni tabella.

3. Selezionare il pulsante **Salva**.

4. Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)