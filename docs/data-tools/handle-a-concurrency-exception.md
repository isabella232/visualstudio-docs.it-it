---
title: Gestire un'eccezione di concorrenza
description: Gestire un'eccezione di concorrenza (System.Data.DBConcurrencyException), che viene generata quando due utenti tentano di modificare gli stessi dati in un database contemporaneamente.
ms.custom: SEO-VS-2020
ms.date: 09/11/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ac64e951c5307d0fe940e6ec92c2e35a727e3811
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075229"
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza

Le eccezioni di concorrenza ( ) vengono generate quando due utenti tentano di modificare contemporaneamente gli stessi dati <xref:System.Data.DBConcurrencyException?displayProperty=fullName> in un database. In questa procedura dettagliata viene creata un'applicazione Windows che illustra come intercettare un oggetto , individuare la riga che ha causato l'errore e apprendere una strategia per <xref:System.Data.DBConcurrencyException> gestirlo.

Questa procedura dettagliata illustra il processo seguente:

1. Creare un nuovo **progetto Windows'applicazione Forms.**

2. Creare un nuovo set di dati basato sulla tabella Northwind Customers.

3. Creare un modulo con un <xref:System.Windows.Forms.DataGridView> oggetto per visualizzare i dati.

4. Compilare un set di dati con i dati della tabella Customers del database Northwind.

5. Usare la **funzionalità Mostra dati** tabella in **Esplora server** accedere ai dati della tabella Customers e modificare un record.

6. Modificare lo stesso record con un valore diverso, aggiornare il set di dati e tentare di scrivere le modifiche nel database, determinando la creazione di un errore di concorrenza.

7. Intercettare l'errore, quindi visualizzare le diverse versioni del record, consentendo all'utente di determinare se continuare e aggiornare il database o annullare l'aggiornamento.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** **Nell'Programma di installazione di Visual Studio** è possibile installare SQL Server Express Local DB come parte  del carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la finestra **SQL Server Esplora oggetti** dati. (SQL Server Esplora oggetti viene installato come parte del carico **di** lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo. Fare clic con il pulsante destro del mouse sull Local DB e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Iniziare creando una nuova applicazione Windows Forms:

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** **o Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop.**

3. Nel riquadro centrale selezionare il tipo di **progetto Windows app Forms.**

4. Assegnare al **progetto il nome ConcurrencyWalkthrough** e quindi scegliere **OK.**

     Il **progetto ConcurrencyWalkthrough** viene creato e aggiunto a **Esplora soluzioni** e viene aperto un nuovo form nella finestra di progettazione.

## <a name="create-the-northwind-dataset"></a>Creare il set di dati Northwind

Creare quindi un set di dati **denominato NorthwindDataSet:**

1. Scegliere **Aggiungi** nuova **origine dati** dal menu Dati .

   Viene avviata la Configurazione guidata origine dati.

2. Nella schermata **Scegliere un tipo di origine dati** selezionare **Database**.

   ![Configurazione guidata origine dati in Visual Studio](media/data-source-configuration-wizard.png)

3. Selezionare una connessione al database di esempio Northwind dall'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco delle connessioni, selezionare **Nuova connessione.**

    > [!NOTE]
    > Se ci si connette a un file di database locale, selezionare **No** quando viene chiesto se si vuole aggiungere il file al progetto.

4. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti.**

5. Espandere il **nodo** Tabelle e selezionare la **tabella** Customers. Il nome predefinito per il set di dati deve **essere NorthwindDataSet.**

6. Selezionare **Fine** per aggiungere il set di dati al progetto.

## <a name="create-a-data-bound-datagridview-control"></a>Creare un controllo DataGridView associato a dati

In questa sezione viene creato un oggetto trascinando l'elemento Customers dalla finestra Origini <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> dati nel form Windows dati.  

1. Per aprire la **finestra Origini** dati, **scegliere** Mostra origini dati dal menu **Dati**.

2. Nella **finestra Origini** dati espandere il **nodo NorthwindDataSet** e quindi selezionare la **tabella** Customers.

3. Selezionare la freccia giù nel nodo della tabella e quindi **selezionare DataGridView** nell'elenco a discesa.

4. Trascinare la tabella in un'area vuota del form.

     Un <xref:System.Windows.Forms.DataGridView> controllo **denominato CustomersDataGridView** e un <xref:System.Windows.Forms.BindingNavigator> controllo denominato **CustomersBindingNavigator** vengono aggiunti al form associato a <xref:System.Windows.Forms.BindingSource> . Questo è, a sua volta, associato alla tabella Customers in NorthwindDataSet.

## <a name="test-the-form"></a>Testare il modulo

È ora possibile testare il modulo per assicurarsi che si comporti come previsto fino a questo punto:

1. Premere **F5 per** eseguire l'applicazione.

     Il modulo viene visualizzato <xref:System.Windows.Forms.DataGridView> con un controllo che contiene i dati della tabella Customers.

2. Selezionare **Arresta debug** dal menu **Debug**.

## <a name="handle-concurrency-errors"></a>Gestire gli errori di concorrenza

La modalità di gestione degli errori dipende dalle regole business specifiche che regolano l'applicazione. Per questa procedura dettagliata viene utilizzata la strategia seguente come esempio per gestire l'errore di concorrenza.

L'applicazione presenta all'utente tre versioni del record:

- Record corrente nel database

- Il record originale caricato nel set di dati

- Modifiche proposte nel set di dati

L'utente può quindi sovrascrivere il database con la versione proposta oppure annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori del database.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza

1. Creare un gestore degli errori personalizzato.

2. Visualizzare le scelte per l'utente.

3. Elaborare la risposta dell'utente.

4. Inviare nuovamente l'aggiornamento o reimpostare i dati nel set di dati.

### <a name="add-code-to-handle-the-concurrency-exception"></a>Aggiungere codice per gestire l'eccezione di concorrenza

Quando si tenta di eseguire un aggiornamento e viene generata un'eccezione, in genere si vuole eseguire un'operazione con le informazioni fornite dall'eccezione generata. In questa sezione viene aggiunto il codice che tenta di aggiornare il database. È anche possibile gestire <xref:System.Data.DBConcurrencyException> qualsiasi eccezione che potrebbe essere generata, nonché qualsiasi altra eccezione.

> [!NOTE]
> I `CreateMessage` metodi e vengono aggiunti più avanti nella procedura `ProcessDialogResults` dettagliata.

1. Aggiungere il codice seguente sotto il `Form1_Load` metodo :

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet1":::

2. Sostituire il `CustomersBindingNavigatorSaveItem_Click` metodo per chiamare il metodo in modo che sia simile al `UpdateDatabase` seguente:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet2":::

### <a name="display-choices-to-the-user"></a>Visualizzare le scelte per l'utente

Il codice appena scritto chiama la `CreateMessage` procedura per visualizzare le informazioni sull'errore all'utente. Per questa procedura dettagliata viene utilizzata una finestra di messaggio per visualizzare le diverse versioni del record all'utente. In questo modo l'utente può scegliere se sovrascrivere il record con le modifiche o annullare la modifica. Quando l'utente seleziona un'opzione (fa clic su un pulsante) nella finestra di messaggio, la risposta viene passata al `ProcessDialogResult` metodo .

Creare il messaggio aggiungendo il codice seguente **all'editor di codice**. Immettere questo codice sotto il `UpdateDatabase` metodo :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet4":::

### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente

È anche necessario codice per elaborare la risposta dell'utente alla finestra di messaggio. Le opzioni disponibili sono sovrascrivere il record corrente nel database con la modifica proposta oppure abbandonare le modifiche locali e aggiornare la tabella di dati con il record attualmente presente nel database. Se l'utente sceglie **Sì,** il <xref:System.Data.DataTable.Merge%2A> metodo viene chiamato con l'argomento *preserveChanges* impostato su **true.** In questo modo il tentativo di aggiornamento ha esito positivo, perché la versione originale del record ora corrisponde al record nel database.

Aggiungere il codice seguente sotto il codice aggiunto nella sezione precedente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs" id="Snippet3":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form-behavior"></a>Testare il comportamento del modulo

È ora possibile testare il modulo per assicurarsi che si comporti come previsto. Per simulare una violazione della concorrenza, modificare i dati nel database dopo aver compilato NorthwindDataSet.

1. Premere **F5 per** eseguire l'applicazione.

2. Quando il modulo viene visualizzato, lasciarlo in esecuzione e passare all'IDE Visual Studio.

3. Scegliere **Esplora server** dal menu **Visualizza**.

4. In **Esplora server** espandere la connessione in uso nell'applicazione e quindi espandere il **nodo** Tabelle .

5. Fare clic con il pulsante destro **del mouse** sulla tabella Customers e quindi scegliere Mostra **dati tabella**.

6. Nel primo record (**ALFKI**) modificare **ContactName** in **Maria Anders2**.

    > [!NOTE]
    > Passare a un'altra riga per eseguire il commit della modifica.

7. Passare al modulo in esecuzione di ConcurrencyWalkthrough.

8. Nel primo record del modulo (**ALFKI**) modificare **ContactName** in **Maria Anders1**.

9. Fare clic sul pulsante **Salva**.

     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.

   Se **si seleziona No,** l'aggiornamento viene annullato e il set di dati viene aggiornato con i valori attualmente presenti nel database. Se **si seleziona Sì,** il valore proposto viene scritto nel database.

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
