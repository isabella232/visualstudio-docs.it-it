---
title: Gestire un'eccezione di concorrenza | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670029"
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vengono generate eccezioni di concorrenza (<xref:System.Data.DBConcurrencyException>) quando due utenti tentano di modificare contemporaneamente gli stessi dati in un database. In questa procedura dettagliata viene creata un'applicazione Windows che illustra come intercettare un <xref:System.Data.DBConcurrencyException>, individuare la riga che ha provocato l'errore e apprendere una strategia per gestirla.

 Questa procedura dettagliata illustra il processo seguente:

1. Creare un nuovo progetto di **applicazione Windows** .

2. Creare un nuovo set di dati in base alla tabella Northwind `Customers`.

3. Creare un modulo con un <xref:System.Windows.Forms.DataGridView> per visualizzare i dati.

4. Compilare un set di dati con i dati della tabella `Customers` nel database Northwind.

5. Utilizzare [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio per accedere direttamente alla tabella dati `Customers` e modificare un record.

6. Modificare lo stesso record con un valore diverso, aggiornare il set di dati e tentare di scrivere le modifiche nel database, causando la generazione di un errore di concorrenza.

7. Rilevare l'errore, quindi visualizzare le diverse versioni del record, consentendo all'utente di determinare se continuare e aggiornare il database o di annullare l'aggiornamento.

## <a name="prerequisites"></a>Prerequisites
 Per completare questa procedura dettagliata, è necessario:

- Accesso al database di esempio Northwind con l'autorizzazione per l'esecuzione di aggiornamenti.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Creare un nuovo progetto
 Per iniziare la procedura dettagliata, è possibile creare una nuova applicazione Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Per creare un nuovo progetto di applicazione Windows

1. Scegliere Crea nuovo progetto dal menu **file** .

2. Nel riquadro **Tipi progetto** selezionare un linguaggio di programmazione.

3. Nel riquadro **modelli** selezionare **applicazione Windows**.

4. Assegnare al progetto il nome `ConcurrencyWalkthrough` e quindi fare clic su **OK**.

     Visual Studio aggiunge il progetto a **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.

## <a name="create-the-northwind-dataset"></a>Creare il set di dati Northwind
 In questa sezione viene creato un set di dati denominato `NorthwindDataSet`.

#### <a name="to-create-the-northwinddataset"></a>Per creare il NorthwindDataSet

1. Scegliere **Aggiungi nuova origine dati**dal menu **dati** .

     Viene avviata la [Configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

2. Nella schermata **scegliere un tipo di origine dati**selezionare **database**.

3. Selezionare una connessione al database di esempio Northwind dall'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco delle connessioni, selezionare**nuova connessione** .

    > [!NOTE]
    > Se ci si connette a un file di database locale, selezionare **No** quando viene richiesto se si desidera aggiungere il file al progetto.

4. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione**selezionare **Avanti**.

5. Espandere il nodo **tabelle** e selezionare la tabella `Customers`. Il nome predefinito del set di dati deve essere `NorthwindDataSet`.

6. Selezionare **fine** per aggiungere il set di dati al progetto.

## <a name="create-a-data-bound-datagridview-control"></a>Creazione di un controllo DataGridView con associazione a dati
 In questa sezione viene creato un <xref:System.Windows.Forms.DataGridView> trascinando l'elemento **Customers** dalla finestra **origini dati** nel Windows Form.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Per creare un controllo DataGridView associato alla tabella Customers

1. Scegliere **Mostra origini dati** dal menu **dati** per aprire la **finestra Origini dati**.

2. Nella finestra **origini dati** espandere il nodo **NorthwindDataSet** , quindi selezionare la tabella **Customers** .

3. Selezionare la freccia rivolta verso il basso sul nodo della tabella, quindi selezionare **DataGridView** nell'elenco a discesa.

4. Trascinare la tabella su un'area vuota del modulo.

     Un controllo <xref:System.Windows.Forms.DataGridView> denominato `CustomersDataGridView` e un <xref:System.Windows.Forms.BindingNavigator> denominato `CustomersBindingNavigator` vengono aggiunti al form associato al <xref:System.Windows.Forms.BindingSource>. questo, è in, viene associato alla tabella `Customers` nel `NorthwindDataSet`.

## <a name="test-the-form"></a>Testare il modulo
 È ora possibile testare il modulo per verificare che il comportamento sia quello previsto fino a questo punto.

#### <a name="to-test-the-form"></a>Per testare il modulo

1. Selezionare **F5** per eseguire l'applicazione

     Il form viene visualizzato con un <xref:System.Windows.Forms.DataGridView> controllo che viene compilato con i dati della tabella `Customers`.

2. Scegliere**Interrompi debug**dal menu **debug** .

## <a name="handleconcurrency-errors"></a>Errori Handleconcurrency
 La modalità di gestione degli errori dipende dalle regole business specifiche che governano l'applicazione. Per questa procedura dettagliata, si userà la strategia seguente come esempio di come gestire l'errore di concorrenza.

 Applicationpresents l'utente con tre versioni del record:

- Record corrente nel database

- Record originale caricato nel set di dati

- Modifiche proposte nel set di dati

  L'utente può quindi sovrascrivere il database con la versione proposta oppure annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori del database.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza

1. Creare un gestore di errori personalizzato.

2. Consente di visualizzare le scelte dell'utente.

3. Elaborare la risposta dell'utente.

4. Inviare di nuovo l'aggiornamento o reimpostare i dati nel set di dati.

### <a name="addcode-to-handle-the-concurrency-exception"></a>AddCode per gestire l'eccezione di concorrenza
 Quando si tenta di eseguire un aggiornamento e viene generata un'eccezione, in genere si desidera eseguire un'operazione con le informazioni fornite dall'eccezione generata.

 In questa sezione viene aggiunto il codice che tenta di aggiornare il database. È anche possibile gestire eventuali <xref:System.Data.DBConcurrencyException> che potrebbero essere generate, nonché qualsiasi altra eccezione.

> [!NOTE]
> I metodi `CreateMessage` e `ProcessDialogResults` verranno aggiunti più avanti in questa procedura dettagliata.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Per aggiungere la gestione degli errori per l'errore di concorrenza

1. Aggiungere il codice seguente sotto il metodo `Form1_Load`:

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` per chiamare il metodo `UpdateDatabase` in modo che abbia un aspetto simile al seguente:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices all'utente
 Il codice appena scritto chiama la procedura `CreateMessage` per visualizzare le informazioni sull'errore all'utente. Per questa procedura dettagliata viene usata una finestra di messaggio per visualizzare le diverse versioni del record per l'utente. Ciò consente all'utente di scegliere se sovrascrivere il record con le modifiche o annullare la modifica. Quando l'utente seleziona un'opzione (fa clic su un pulsante) nella finestra di messaggio, la risposta viene passata al metodo `ProcessDialogResult`.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Per creare il messaggio da visualizzare all'utente

- Creare il messaggio aggiungendo il codice seguente all'editor di **codice**. Immettere questo codice sotto il metodo `UpdateDatabase`.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente
 È necessario anche codice per elaborare la risposta dell'utente alla finestra di messaggio. Le opzioni consentono di sovrascrivere il record corrente nel database con la modifica proposta oppure di abbandonare le modifiche locali e aggiornare la tabella dati con il record attualmente presente nel database. Se l'utente sceglie Sì, il metodo <xref:System.Data.DataTable.Merge%2A> viene chiamato con l'argomento *preserveChanges* impostato su `true`. In questo modo il tentativo di aggiornamento ha esito positivo, perché la versione originale del record ora corrisponde al record nel database.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Per elaborare l'input dell'utente dalla finestra di messaggio

- Aggiungere il codice seguente sotto il codice aggiunto nella sezione precedente.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testare il modulo
 È ora possibile testare il form per assicurarsi che si comportano come previsto. Per simulare una violazione della concorrenza, è necessario modificare i dati nel database dopo aver compilato l'oggetto NorthwindDataSet.

#### <a name="to-test-the-form"></a>Per testare il modulo

1. Selezionare **F5** per eseguire l'applicazione.

2. Una volta visualizzato il modulo, lasciarlo in esecuzione e passare all'IDE di Visual Studio.

3. Scegliere **Esplora server**dal menu **Visualizza** .

4. In **Esplora server**espandere la connessione usata dall'applicazione, quindi espandere il nodo **tabelle** .

5. Fare clic con il pulsante destro del mouse sulla tabella **Customers** , quindi scegliere **Mostra dati tabella**.

6. Nel primo record (`ALFKI`) modificare `ContactName` `Maria Anders2`.

    > [!NOTE]
    > Passare a una riga diversa per eseguire il commit della modifica.

7. Passa al modulo in esecuzione `ConcurrencyWalkthrough`.

8. Nel primo record del modulo (`ALFKI`) modificare `ContactName` in `Maria Anders1`.

9. Selezionare il pulsante **Salva**.

     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.

10. Se si seleziona **No** , l'aggiornamento viene annullato e il set di dati viene aggiornato con i valori attualmente presenti nel database. Se **si seleziona Sì** , il valore proposto viene scritto nel database.

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)