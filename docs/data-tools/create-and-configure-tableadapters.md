---
title: Creare e configurare oggetti TableAdapter
ms.date: 09/01/2017
ms.topic: conceptual
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f1403d61dd7a0d36401e449806fdafa6adc533b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648609"
---
# <a name="create-and-configure-tableadapters"></a>Creare e configurare oggetti TableAdapter

Gli oggetti TableAdapter forniscono la comunicazione tra l'applicazione e un database. Si connettono al database, eseguono query o stored procedure e restituiscono una nuova tabella di dati o compilano un <xref:System.Data.DataTable> esistente con i dati restituiti. Gli oggetti TableAdapter possono anche inviare dati aggiornati dall'applicazione al database.

Gli oggetti TableAdapter vengono creati automaticamente quando si esegue una delle azioni seguenti:

- Trascinare oggetti di database da **Esplora server** nel **Progettazione DataSet**.

- Eseguire la configurazione guidata origine dati e selezionare il tipo di origine dati del **database** o del **servizio Web** .

   ![Configurazione guidata origine dati in Visual Studio](media/data-source-configuration-wizard.png)

È anche possibile creare un nuovo TableAdapter e configurarlo con un'origine dati trascinando un TableAdapter dalla **casella degli strumenti** in un'area vuota dell'area di **Progettazione DataSet** .

Per un'introduzione agli oggetti TableAdapter, vedere [Fill DataSets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Usare la configurazione guidata TableAdapter

Eseguire la **Configurazione guidata TableAdapter** per creare o modificare TableAdapter e le relative DataTable associate. È possibile configurare un TableAdapter esistente facendo clic con il pulsante destro del mouse sul **Progettazione DataSet**.

![Configurazione guidata adattatore tabella raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Se si trascina un nuovo TableAdapter dalla casella degli strumenti quando il **Progettazione DataSet** è attivo, viene avviata la procedura guidata e viene richiesto di specificare l'origine dati a cui deve connettersi il TableAdapter. Nella pagina successiva la procedura guidata richiede il tipo di comandi da usare per comunicare con il database, ovvero le istruzioni SQL o le stored procedure. Non verrà visualizzato se si sta configurando un TableAdapter già associato a un'origine dati.

- È possibile scegliere di creare un nuovo stored procedure nel database sottostante se si dispone delle autorizzazioni corrette per il database. Se non si dispone di queste autorizzazioni, questa non sarà un'opzione.

- È inoltre possibile scegliere di eseguire stored procedure esistenti per i comandi **Select**, **Insert**, **Update**e **Delete** del TableAdapter. Il stored procedure assegnato al comando **Update** , ad esempio, viene eseguito quando viene chiamato il metodo `TableAdapter.Update()`.

Mappare i parametri dalla stored procedure selezionata alle colonne corrispondenti nella tabella dati. Se, ad esempio, il stored procedure accetta un parametro denominato `@CompanyName` che passa alla colonna `CompanyName` della tabella, impostare la colonna di **origine** del parametro `@CompanyName` su `CompanyName`.

> [!NOTE]
> La stored procedure assegnata al comando SELECT viene eseguita chiamando il metodo dell'oggetto TableAdapter denominato nel passaggio successivo della procedura guidata. Il metodo predefinito è `Fill`, quindi il codice usato in genere per eseguire la procedura di selezione è `TableAdapter.Fill(tableName)`. Se si modifica il nome predefinito da `Fill`, sostituire `Fill` con il nome assegnato e sostituire "TableAdapter" con il nome effettivo del TableAdapter (ad esempio, `CustomersTableAdapter`).

- La selezione dell'opzione **Crea metodi per inviare aggiornamenti direttamente al database** equivale a impostare la proprietà `GenerateDBDirectMethods` su true. Questa opzione non è disponibile quando l'istruzione SQL originale non fornisce informazioni sufficienti o se la query non è aggiornabile. Questa situazione può verificarsi, ad esempio, in query **join** e query che restituiscono un singolo valore (scalare).

Le **Opzioni avanzate** della procedura guidata consentono di:

- Genera istruzioni INSERT, UPDATE e DELETE in base all'istruzione SELECT definita nella pagina **genera istruzioni SQL**
- Usa concorrenza ottimistica
- Consente di specificare se aggiornare la tabella dati dopo l'esecuzione delle istruzioni INSERT e UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Configurare il metodo Fill di un TableAdapter

In alcuni casi potrebbe essere necessario modificare lo schema della tabella del TableAdapter. A tale scopo, modificare il metodo di `Fill` primario del TableAdapter. Gli oggetti TableAdapter vengono creati con un metodo di `Fill` primario che definisce lo schema della tabella di dati associata. Il metodo di `Fill` primario è basato sulla query o stored procedure immesso al momento della configurazione iniziale del TableAdapter. Si tratta del primo metodo (in primo piano) nella tabella dati in Progettazione DataSet.

![TableAdapter con più query](../data-tools/media/tableadapter.gif)

Tutte le modifiche apportate al metodo `Fill` principale del TableAdapter si riflettono nello schema della tabella dati associata. Se ad esempio si rimuove una colonna dalla query nel metodo Main `Fill`, viene rimossa anche la colonna dalla tabella di dati associata. Inoltre, la rimozione della colonna dal metodo Main `Fill` rimuove la colonna da eventuali query aggiuntive per tale TableAdapter.

È possibile utilizzare la configurazione guidata query TableAdapter per creare e modificare query aggiuntive per il TableAdapter. Queste query aggiuntive devono essere conformi allo schema della tabella, a meno che non restituiscano un valore scalare.  Ogni query aggiuntiva ha un nome specificato.

Nell'esempio seguente viene illustrato come chiamare una query aggiuntiva denominata `FillByCity`:

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Per avviare la configurazione guidata query TableAdapter con una nuova query

1. Aprire il set di dati in **Progettazione DataSet**.

2. Se si sta creando una nuova query, trascinare un oggetto **query** dalla scheda **DataSet** della **casella degli strumenti** in un <xref:System.Data.DataTable> oppure selezionare **Aggiungi query** dal menu di scelta rapida del TableAdapter. È anche possibile trascinare un oggetto **query** su un'area vuota del **Progettazione DataSet**, che crea un TableAdapter senza una <xref:System.Data.DataTable> associata. Queste query possono restituire solo valori singoli (scalari) o eseguire comandi di aggiornamento, inserimento o eliminazione sul database.

3. Nella schermata **Seleziona connessione dati** selezionare o creare la connessione che viene utilizzata dalla query.

    > [!NOTE]
    > Questa schermata viene visualizzata solo quando la finestra di progettazione non è in grado di determinare la connessione appropriata da utilizzare o se non sono disponibili connessioni.

4. Nella schermata **scegliere un tipo di comando selezionare uno** dei metodi seguenti per recuperare i dati dal database:

    - **Usa istruzioni SQL** consente di digitare un'istruzione SQL per selezionare i dati dal database.

    - **Crea nuovo stored procedure** consente di fare in modo che la procedura guidata crei una nuova stored procedure (nel database) basata sull'istruzione SELECT specificata.

    - **Usa stored procedure esistenti** consente di eseguire una stored procedure esistente quando si esegue la query.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Per avviare la configurazione guidata query TableAdapter in una query esistente

- Se si sta modificando una query TableAdapter esistente, fare clic con il pulsante destro del mouse sulla query, quindi scegliere **Configura** dal menu di scelta rapida.

    > [!NOTE]
    > Facendo clic con il pulsante destro del mouse sulla query principale di un TableAdapter vengono riconfigurati lo schema TableAdapter e <xref:System.Data.DataTable>. Tuttavia, facendo clic con il pulsante destro del mouse su una query aggiuntiva su un TableAdapter, viene configurata solo la query selezionata. La **Configurazione guidata TableAdapter** consente di riconfigurare la definizione TableAdapter, mentre la **Configurazione guidata query TableAdapter** riconfigura solo la query selezionata.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Per aggiungere una query globale a un TableAdapter

- Le query globali sono query SQL che restituiscono un singolo valore (scalare) o nessun valore. In genere, le funzioni globali eseguono operazioni di database, ad esempio inserimenti, aggiornamenti ed eliminazioni. Vengono inoltre aggregate informazioni, ad esempio un conteggio dei clienti in una tabella o gli addebiti totali per tutti gli elementi in un ordine specifico.

     Per aggiungere query globali, trascinare un oggetto **query** dalla scheda **DataSet** della **casella degli strumenti** su un'area vuota del **Progettazione DataSet**.

- Fornire una query che esegua l'attività desiderata, ad esempio `SELECT COUNT(*) AS CustomerCount FROM Customers`.

    > [!NOTE]
    > Il trascinamento di un oggetto **query** direttamente sul **Progettazione DataSet** crea un metodo che restituisce solo un valore scalare (singolo). Mentre la query o la stored procedure selezionata potrebbe restituire più di un valore singolo, il metodo creato dalla procedura guidata restituisce solo un valore singolo. Ad esempio, la query potrebbe restituire la prima colonna della prima riga dei dati restituiti.

## <a name="see-also"></a>Vedere anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)