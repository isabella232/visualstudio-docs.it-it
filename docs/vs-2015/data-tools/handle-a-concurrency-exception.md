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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7ee82187adac74f90b6f5cb8485c68452d8329b0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060710"
---
# <a name="handle-a-concurrency-exception"></a>Gestire un'eccezione di concorrenza
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le eccezioni di concorrenza (<xref:System.Data.DBConcurrencyException>) vengono generati quando due utenti tentano di modificare gli stessi dati in un database nello stesso momento. In questa procedura dettagliata, si crea un'applicazione Windows che illustra come intercettare una <xref:System.Data.DBConcurrencyException>, individuare la riga che ha causato l'errore e informazioni su una strategia per come gestirlo.  
  
 Questa procedura dettagliata illustra il processo seguente:  
  
1. Creare una nuova **applicazioni Windows** progetto.  
  
2. Creare un nuovo set di dati basato su Northwind `Customers` tabella.  
  
3. Creare un form con un <xref:System.Windows.Forms.DataGridView> per visualizzare i dati.  
  
4. Inserire dati da un set di dati di `Customers` tabella nel database Northwind.  
  
5. Usare la [Visual Database Tools](http://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) in Visual Studio per accedere direttamente il `Customers` dati tabella e modificare un record.  
  
6. Modificare lo stesso record su un valore diverso, aggiornare il set di dati e tentano di scrivere le modifiche al database, che comporta un errore di concorrenza.  
  
7. Intercetta l'errore, quindi visualizzare le diverse versioni del record, consentendo all'utente determinare se per continuare e aggiornare il database oppure per annullare l'aggiornamento.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
- Accesso al database Northwind di esempio con l'autorizzazione per eseguire gli aggiornamenti.
  
> [!NOTE]
>  Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o l'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Creare un nuovo progetto  
 Iniziare la procedura dettagliata creando una nuova applicazione Windows.  
  
#### <a name="to-create-a-new-windows-application-project"></a>Per creare un nuovo progetto applicazione Windows  
  
1. Nel **File** menu, creare un nuovo progetto.  
  
2. Nel **tipi di progetto** riquadro, selezionare un linguaggio di programmazione.  
  
3. Nel **modelli** riquadro, selezionare **applicazioni Windows**.  
  
4. Denominare il progetto `ConcurrencyWalkthrough`, quindi selezionare **OK**.  
  
     Visual Studio aggiunge il progetto **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.  
  
## <a name="create-the-northwind-dataset"></a>Creare il set di dati di Northwind  
 In questa sezione si crea un set di dati denominato `NorthwindDataSet`.  
  
#### <a name="to-create-the-northwinddataset"></a>Creazione di NorthwindDataSet  
  
1. Nel **Data** menu, scegliere **origine aggiungere nuovi dati**.  
  
     Viene avviata la [Configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
2. Nel **scegliere un tipo di origine dati**schermata, seleziona **Database**.  
  
3. Selezionare una connessione al database di esempio Northwind nell'elenco delle connessioni disponibili. Se la connessione non è disponibile nell'elenco delle connessioni, selezionare**nuova connessione**  
  
    > [!NOTE]
    >  Se ci si connette a un file di database locale, selezionare **No** quando viene chiesto se si desidera aggiungere il file al progetto.  
  
4. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione**schermata, seleziona **successivo**.  
  
5. Espandere la **tabelle** nodo e selezionare il `Customers` tabella. Il nome predefinito per il set di dati deve essere `NorthwindDataSet`.  
  
6. Selezionare **fine** per aggiungere il set di dati al progetto.  
  
## <a name="create-a-data-bound-datagridview-control"></a>Creare un controllo DataGridView associato ai dati  
 In questa sezione si crea una <xref:System.Windows.Forms.DataGridView> trascinando la **clienti** articolo dal **Zdroje dat** finestra nei Form Windows.  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Per creare un controllo DataGridView associato alla tabella Customers  
  
1. Nel **Data** menu, scegliere **Mostra origini dati** per aprire la **finestra Origini dati**.  
  
2. Nel **Zdroje dat** finestra, espandere il **NorthwindDataSet** nodo e quindi selezionare il **clienti** tabella.  
  
3. Selezionare la freccia rivolta verso il basso nel nodo della tabella e quindi selezionare **DataGridView** nell'elenco a discesa.  
  
4. Trascinare la tabella in un'area vuota del form.  
  
     Oggetto <xref:System.Windows.Forms.DataGridView> controllo denominato `CustomersDataGridView` e un <xref:System.Windows.Forms.BindingNavigator> denominato `CustomersBindingNavigator` vengono aggiunti al form che è associato il <xref:System.Windows.Forms.BindingSource>. Si tratta, attivare associato ai `Customers` nella tabella il `NorthwindDataSet`.  
  
## <a name="test-the-form"></a>Verificare il modulo  
 È ora possibile testare il form per assicurarsi che tutto funzioni come previsto fino a questo punto.  
  
#### <a name="to-test-the-form"></a>Per testare il form  
  
1. Selezionare **F5** per eseguire l'applicazione  
  
     Viene visualizzato il form con un <xref:System.Windows.Forms.DataGridView> controllo su di esso viene riempita con i dati di `Customers` tabella.  
  
2. Nel **Debug** dal menu**arresta debug**.  
  
## <a name="handleconcurrency-errors"></a>Errori Handleconcurrency  
 La gestione degli errori dipende dalle regole business specifici che regolano l'applicazione. Per questa procedura dettagliata, utilizziamo la strategia seguente come esempio per come tohandle l'errore di concorrenza.  
  
 L'utente con le tre versioni del record di applicationpresents:  
  
- Il record corrente nel database  
  
- Il record originale che viene caricato nel set di dati  
  
- Le modifiche proposte nel set di dati  
  
  L'utente è quindi possibile sovrascrivere il database con la versione proposta, o annullare l'aggiornamento e aggiornare il set di dati con i nuovi valori dal database.  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Per abilitare la gestione degli errori di concorrenza  
  
1. Creare un gestore errori personalizzato.  
  
2. Visualizzare le scelte per l'utente.  
  
3. Elaborare la risposta dell'utente.  
  
4. Inviare di nuovo l'aggiornamento o ripristinare i dati nel set di dati.  
  
### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode per gestire l'eccezione di concorrenza  
 Quando si tenta di eseguire un aggiornamento e viene generata un'eccezione, in genere si desidera eseguire un'operazione con le informazioni fornite per l'eccezione generata.  
  
 In questa sezione si aggiunta il codice che tenta di aggiornare il database. È anche possibile gestire qualsiasi <xref:System.Data.DBConcurrencyException> che potrebbero ottenere generati, oltre a qualsiasi altra eccezione.  
  
> [!NOTE]
>  Il `CreateMessage` e `ProcessDialogResults` metodi verranno aggiunti più avanti in questa procedura dettagliata.  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Per aggiungere Gestione degli errori per l'errore di concorrenza  
  
1. Aggiungere il codice seguente sotto il `Form1_Load` metodo:  
  
     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]  
  
2. Sostituire il `CustomersBindingNavigatorSaveItem_Click` metodo da chiamare il `UpdateDatabase` metodo in modo che risulti simile al seguente:  
  
     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]  
  
### <a name="displaychoices-to-the-user"></a>Displaychoices all'utente  
 Il codice sopra riportato consente le chiamate di `CreateMessage` procedura per visualizzare le informazioni sull'errore all'utente. In questa procedura dettagliata si usa una finestra di messaggio per visualizzare le diverse versioni del record per l'utente. Ciò consente all'utente di scegliere se si desidera sovrascrivere il record con le modifiche oppure annullare la modifica. Una volta che l'utente seleziona un'opzione (Seleziona un pulsante) nella finestra di messaggio, la risposta viene passata per il `ProcessDialogResult` (metodo).  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>Per creare il messaggio da visualizzare all'utente  
  
- Creare il messaggio aggiungendo il codice seguente per il **Editor di codice**. Immettere il codice riportato di seguito il `UpdateDatabase` (metodo).  
  
     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]  
  
### <a name="process-the-users-response"></a>Elaborare la risposta dell'utente  
 È anche necessario codice per elaborare la risposta dell'utente nella finestra di messaggio. Le opzioni sono a sovrascrivere il record corrente nel database con la modifica proposta, o ignorare le modifiche locali e aggiornare la tabella di dati con il record che è attualmente nel database. Se l'utente sceglie Sì, il <xref:System.Data.DataTable.Merge%2A> metodo viene chiamato con il *preserveChanges* argomento impostato su `true`. In questo modo il tentativo di aggiornamento abbia esito positivo, perché la versione originale del record corrisponde a questo punto il record nel database.  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>Per elaborare l'utente di input nella finestra di messaggio  
  
- Aggiungere il codice seguente sotto il codice che è stato aggiunto nella sezione precedente.  
  
     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Verificare il modulo  
 È ora possibile testare il form per assicurarsi che tutto funzioni come previsto. Per simulare una violazione della concorrenza che è necessario modificare i dati nel database dopo aver compilato NorthwindDataSet.  
  
#### <a name="to-test-the-form"></a>Per testare il form  
  
1. Selezionare **F5** per eseguire l'applicazione.  
  
2. Una volta visualizzato il form, lascia in esecuzione e passare all'IDE di Visual Studio.  
  
3. Nel **View** menu, scegliere **Esplora Server**.  
  
4. Nelle **Esplora Server**, espandere la connessione viene usando l'applicazione e quindi espandere il **tabelle** nodo.  
  
5. Fare doppio clic il **clienti** tabella e quindi selezionare **Mostra dati tabella**.  
  
6. Nel primo record (`ALFKI`) cambiare `ContactName` a `Maria Anders2`.  
  
    > [!NOTE]
    >  Passare a un'altra riga per il commit della modifica.  
  
7. Passare al `ConcurrencyWalkthrough`form in esecuzione.  
  
8. Nel primo record nel form (`ALFKI`), cambiare`ContactName` a `Maria Anders1`.  
  
9. Selezionare il pulsante **Salva**.  
  
     Viene generato l'errore di concorrenza e viene visualizzata la finestra di messaggio.  
  
10. Selezionando **No** Annulla l'aggiornamento e aggiorna il set di dati con i valori presenti nel database. Selezionando **Sì** scrive il valore proposto per il database.
  
## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)