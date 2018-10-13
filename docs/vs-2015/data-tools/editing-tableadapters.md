---
title: Modifica di TableAdapter | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.dbtablefunctionwizard
- vs.datasource.datacomponentquerywizard
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], data component queries
- data [Visual Studio], TableAdapters
- TableAdapter Query Configuration Wizard
- data [Visual Studio], table adapter queries
ms.assetid: 8c06b306-24d0-4521-948d-07e3b7badd95
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: faeac90c92675c897774cc3650575cd60f5be991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288405"
---
# <a name="editing-tableadapters"></a>Modifica di TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcuni casi si potrebbe voler modificare lo schema della tabella dell'adapter. A tale scopo, si modifica primario dell'adapter `Fill` (metodo). TableAdapter vengono creati con una funzione main `Fill` metodo che definisce lo schema della tabella dati associata. Principale `Fill` metodo si basa sulla query o stored procedure immesse durante la configurazione iniziale del TableAdapter; è il primo metodo (in primo piano) sotto la tabella di dati sul [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
 ![TableAdapter con più query](../data-tools/media/tableadapter.gif "TableAdapter")  
  
 Tutte le modifiche apportate all'oggetto TableAdapter principale del `Fill` metodo vengono riflesse nello schema della tabella dati associata. Ad esempio la rimozione di una colonna dalla query principale `Fill` metodo rimuove anche la colonna dalla tabella dati associata. Inoltre, rimuovere la colonna dalla principale `Fill` metodo rimuove la colonna da qualsiasi altra query per tale oggetto TableAdapter.  
  
 È possibile usare la **configurazione guidata Query TableAdapter** per creare e modificare query aggiuntive per l'oggetto TableAdapter. Queste query aggiuntive devono essere conformi allo schema della tabella, a meno che non restituiscono un valore scalare.  Le ulteriori query che hanno un nome specificato (ad esempio, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`.)  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Per avviare la configurazione guidata Query TableAdapter con una nuova query  
  
1.  Aprire il set di dati nel **Progettazione Dataset**.  
  
2.  Se si sta creando una nuova query, trascinare un **Query** dall'oggetto il **set di dati** scheda della finestra di **della casella degli strumenti** in un <xref:System.Data.DataTable>, o selezionare **Aggiungi Query**dal menu di scelta rapida dell'oggetto TableAdapter. È anche possibile trascinare un **Query** oggetto in un'area vuota del **Progettazione Dataset**, che consente di creare un oggetto non associato a un TableAdapter <xref:System.Data.DataTable>. Queste query sono limitate per la restituzione di valori singoli (scalari) o l'esecuzione di UPDATE, INSERT o DELETE comandi sul database. Per altre informazioni, vedere [procedura: aggiungere query globali a un oggetto TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).  
  
3.  Nel **Seleziona connessione dati** pagina selezionare o creare la connessione utilizzerà la query.  
  
    > [!NOTE]
    >  Questa pagina viene visualizzata solo quando la finestra di progettazione non è possibile stabilire la connessione appropriata da utilizzare oppure quando non vi sono connessioni disponibili.  
  
4.  Nel **scegliere un tipo di comando** pagina, selezionare uno dei seguenti metodi di recupero dei dati dal database:  
  
    -   **Usare le istruzioni SQL** consente di digitare un'istruzione SQL per selezionare i dati dal database.  
  
    -   **Crea nuova stored procedure** : selezionare questa opzione per indicare alla procedura guidata crea una nuova stored procedure (nel database) in base all'istruzione SELECT specificata.  
  
    -   **Usare le stored procedure esistenti** : selezionare questa opzione per eseguire una stored procedure esistente quando si esegue la query.  
  
#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Per avviare la configurazione guidata Query TableAdapter in una query esistente  
  
-   Se si sta modificando una query TableAdapter esistente, fare doppio clic su query e scegliere **configura** dal menu di scelta rapida.  
  
    > [!NOTE]
    >  Pulsante destro del mouse la query principale di un oggetto TableAdapter riconfigura TableAdapter e <xref:System.Data.DataTable> dello schema, mentre una query aggiuntiva in un oggetto TableAdapter consente di configurare solo la query selezionata. Il **configurazione guidata TableAdapter** riconfigura la definizione del TableAdapter; gli **configurazione guidata Query TableAdapter** riconfigura solo la query selezionata.  
  
## <a name="running-the-wizard"></a>Esecuzione della procedura guidata  
 Trascinare le query nella **Progettazione Dataset**, oppure configurare quelle esistenti (qualsiasi query elencate di seguito la prima query).  
  
 La prima query in un oggetto TableAdapter è la query TableAdapter principale. Se tale query consente di aprire la **configurazione guidata TableAdapter** e modificato lo schema della tabella di dati dell'oggetto TableAdapter. Tutte le query elencate di seguito la query principale sono query aggiuntive e vengono configurate tramite il **configurazione guidata Query TableAdapter**. Per altre informazioni su esecuzione della procedura guidata, vedere [procedura: avviare la configurazione guidata Query TableAdapter](http://msdn.microsoft.com/library/fc7b468e-3417-48a4-a8aa-cace8f99c24a).  
  
## <a name="choose-your-data-connection"></a>Selezione della connessione dati  
 Scegliere una connessione esistente dall'elenco di connessioni oppure fare clic su **nuova connessione** per creare una connessione al database.  
  
 Al completamento dei **le proprietà di connessione** della finestra di dialogo il **i dettagli della connessione** area Visualizza le informazioni di sola lettura sul provider selezionato, nonché la stringa di connessione.  
  
## <a name="save-the-connection-string-to-the-application-configuration-file"></a>Salvataggio della stringa di connessione nel file di configurazione dell'applicazione  
 Scegli **Sì, Salva la connessione come** per archiviare la stringa di connessione nel file di configurazione dell'applicazione. Digitare un nome per la connessione oppure usare il nome predefinito.  
  
 Salvando le stringhe di connessione nel file di configurazione dell'applicazione, è possibile semplificare il processo di gestione dell'applicazione se la connessione di database cambia. Se la connessione al database viene modificata, è possibile modificare la stringa di connessione nel file di configurazione dell'applicazione. In questo modo non sarà necessario modificare il codice sorgente e ricompilare l'applicazione. Per informazioni su come modificare una stringa di connessione nel file di configurazione dell'applicazione, vedere [procedura: salvare e modificare le stringhe di connessione](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
> [!IMPORTANT]
>  Le informazioni vengono archiviate nel file di configurazione dell'applicazione come testo normale. Per ridurre la possibilità di un accesso non autorizzato a informazioni riservate, è possibile crittografare i dati. Per altre informazioni, vedere [crittografia e la decrittografia dei dati](http://msdn.microsoft.com/en-us/22812ae8-e082-4eb1-a29b-21b6ee00c6b5).  
  
## <a name="use-sql-statements"></a>Usa istruzioni SQL  
 In questa sezione descrive come completare la **configurazione guidata Query TableAdapter** quando si seleziona il **Usa istruzioni SQL** opzione.  
  
## <a name="choose-a-query-type"></a>Scegli tipo di query  
 La procedura guidata consente di creare diversi tipi di query in base ai requisiti dell'applicazione. È possibile scegliere query SELECT che restituiscono righe di dati (una tabella dati) o query SELECT che restituiscono un valore scalare (un singolo valore come `Count` o `Sum`).  
  
 Nel **scegliere un tipo di Query** pagina, selezionare il tipo di query per creare dall'elenco di query disponibili.  
  
> [!NOTE]
>  La creazione di un'istruzione INSERT, UPDATE o DELETE non comporta la sostituzione dei comandi dell'oggetto TableAdapter usati quando si chiama il relativo metodo `Update`. Se ad esempio si seleziona il tipo di query UPDATE, verrà creata una nuova query con un nome specificato successivamente nella procedura guidata. Per eseguire la query è necessario chiamare questo metodo denominato dell'oggetto TableAdapter. Chiamando il metodo `Update` dell'oggetto TableAdapter verranno eseguite le istruzioni create al momento della configurazione dell'oggetto originale.  
  
## <a name="specify-a-sql-query-type-statement"></a>Specificare un database SQL \<tipo Query > istruzione  
 Nel **specificare un'istruzione SQL** , digitare l'istruzione SQL da eseguire quando si chiama la query.  
  
> [!TIP]
>  La procedura guidata fornisce l'accesso per il **generatore Query**, uno strumento visivo per la creazione di query SQL. Per aprirlo, fare clic sui **generatore Query** pulsante.  
  
## <a name="choose-methods-to-generate"></a>Scegliere i metodi per generare  
 Questa pagina contiene le opzioni per la selezione dei metodi da generare per la query mediante la procedura guidata.  
  
 **Riempi un DataTable**  
 Crea un metodo per il riempimento della tabella dati. Quando si chiama questo metodo per riempire la tabella dati con i dati restituiti, il nome della tabella viene passato come parametro.  
  
 Facoltativamente, è possibile modificare il nome predefinito nel **nome del metodo** casella. Specificare un nome significativo può risultare utile quando la query viene usata in una stringa di codice.  
  
 **Restituisci un DataTable**  
 Crea un metodo per la restituzione di una tabella dati popolata. In alcune applicazioni è preferibile restituire una tabella dati compilata invece di riempire con dati la tabella dati esistente.  
  
 Facoltativamente, è possibile modificare il nome predefinito nel **nome del metodo** casella.  
  
## <a name="choose-function-name"></a>Scegli il nome della funzione  
 Digitare un nome per la funzione. La creazione di una query TableAdapter comporta l'aggiunta all'oggetto TableAdapter di un metodo con il nome specificato. Chiamare questo metodo per eseguire la query. Specificare un nome significativo è utile quando la query viene usata in una stringa di codice.  
  
> [!NOTE]
>  Durante la creazione di nuove stored procedure, viene richiesto di immettere due nomi. Il primo è il nome della stored procedure creata nel database, il secondo è il nome del metodo dell'oggetto TableAdapter che esegue la stored procedure quando viene chiamato.  
  
## <a name="create-new-stored-procedures"></a>Creare nuove stored procedure  
 In questa sezione descrive come completare la **configurazione guidata Query TableAdapter** quando si seleziona il **crea nuove stored procedure** opzione.  
  
1.  Nel **genera le Stored procedure** , digitare l'istruzione SQL da eseguire quando viene chiamata la stored procedure.  
  
    > [!NOTE]
    >  La procedura guidata fornisce l'accesso per il **generatore Query**, uno strumento visivo per la creazione di query SQL. Per aprirlo, fare clic sui **generatore Query** pulsante.  
  
2.  Nel **creare le stored procedure** pagina, effettuare le operazioni seguenti:  
  
    1.  Digitare un nome per la nuova stored procedure.  
  
    2.  Specificare se creare la stored procedure nel database sottostante.  
  
        > [!NOTE]
        >  La possibilità di creare una stored procedure nel database dipende dalle impostazioni di sicurezza dello specifico database.  
  
     Il **visualizzare i risultati della procedura guidata** pagina Mostra i risultati della creazione della query TableAdapter. Se nel corso della procedura si verificano problemi, in questa pagina vengono visualizzate le informazioni sugli errori.  
  
## <a name="use-existing-stored-procedures"></a>Usa stored procedure esistenti  
 In questa sezione descrive come completare la **configurazione guidata Query TableAdapter** quando si seleziona il **utilizzare le stored procedure esistenti** opzione.  
  
1.  Selezionare una stored procedure esistente dall'elenco a discesa scegliere nella **sceglie una stored procedure esistente** pagina della procedura guidata.  
  
     Il **parametri** e **risultati** per selezionato stored procedure vengono visualizzati per riferimento.  
  
2.  Scegliere **Avanti**.  
  
## <a name="choose-the-shape-of-data-returned-by-the-stored-procedure"></a>Scegliere la forma dei dati restituiti dalla stored procedure  
 Il tipo di dati restituiti dalla stored procedure selezionata determina la modalità di creazione dei metodi dell'oggetto TableAdapter mediante la procedura guidata.  
  
 Selezionare il tipo di dati restituiti da questa query.  
  
-   Selezionando **TSD** consente di aprire il **scegliere i metodi per generare** pagina (descritta in precedenza in questa pagina della Guida in linea), che consente di specificare i tipi di metodi, i nomi dei metodi e supporto per lo spostamento da creare.  
  
-   Selezionando **un singolo valore** crea un metodo tipizzato che restituisce un valore singolo. Questa opzione consente di aprire la **Scegli nome funzione** pagina (descritta in precedenza in questa pagina della Guida).  
  
-   Selezionando **alcun valore** crea un metodo tipizzato che esegue la stored procedure e si aspetta che nessun dato da restituire. Questa opzione consente di aprire la **Scegli nome funzione** pagina (descritta in precedenza in questa pagina della Guida).  
  
## <a name="view-wizards-results"></a>Risultati procedura guidata  
 Il **visualizzare i risultati della procedura guidata** pagina Mostra i risultati della creazione della query TableAdapter. Se nel corso della procedura si verificano problemi, in questa pagina vengono visualizzate le relative informazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Panoramica delle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)