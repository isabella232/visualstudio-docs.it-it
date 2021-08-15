---
title: Creare e configurare oggetti TableAdapter
description: Vedere come creare e configurare un oggetto TableAdapter in Visual Studio. Gli oggetti TableAdapter forniscono la comunicazione tra l'applicazione e un database.
ms.custom: SEO-VS-2020
ms.date: 09/01/2017
ms.topic: how-to
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 024511b6bec5d060018c2a4976b17d22357ccaa8789a716af14debb037e91169
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347474"
---
# <a name="create-and-configure-tableadapters"></a>Creare e configurare oggetti TableAdapter

Gli oggetti TableAdapter forniscono la comunicazione tra l'applicazione e un database. Si connettono al database, eseguono query o stored procedure e restituiscono una nuova tabella di dati o riempiono un oggetto esistente <xref:System.Data.DataTable> con i dati restituiti. I TableAdapter possono anche inviare dati aggiornati dall'applicazione al database.

Gli oggetti TableAdapter vengono creati automaticamente quando si esegue una delle azioni seguenti:

- Trascinare gli oggetti **di database Esplora server** nella **Progettazione DataSet**.

- Eseguire la Configurazione guidata origine dati e selezionare il tipo di origine dati **Database** o **Servizio Web.**

   ![Configurazione guidata origine dati in Visual Studio](media/data-source-configuration-wizard.png)

È anche possibile creare un nuovo TableAdapter e configurarlo con  un'origine dati trascinando un oggetto TableAdapter dalla Casella degli **strumenti** in un'area vuota nella Progettazione DataSet dati.

Per un'introduzione ai TableAdapter, vedere [Riempire set di dati tramite TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Usare la Configurazione guidata TableAdapter

Eseguire la **Configurazione guidata TableAdapter** per creare o modificare oggetti TableAdapter e le datatable associate. È possibile configurare un TableAdapter esistente facendo clic con il pulsante destro del mouse su di esso **nella** Progettazione DataSet .

![Configurazione guidata adattatore tabella raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

Se si trascina un nuovo oggetto TableAdapter dalla casella degli strumenti quando il **Progettazione DataSet** è attivo, viene avviata la procedura guidata e viene richiesto di specificare l'origine dati a cui deve connettersi l'oggetto TableAdapter. Nella pagina successiva, la procedura guidata chiede quale tipo di comandi deve usare per comunicare con il database, SQL istruzioni o stored procedure. Questa operazione non verrà visualizzata se si configura un oggetto TableAdapter già associato a un'origine dati.

- È possibile creare un nuovo stored procedure nel database sottostante se si dispone delle autorizzazioni corrette per il database. Se non si dispone di queste autorizzazioni, questa non sarà un'opzione.

- È anche possibile scegliere di eseguire stored procedure esistenti per i **comandi SELECT**, **INSERT**, **UPDATE** e **DELETE** del TableAdapter. Il stored procedure assegnato al comando **Update,** ad esempio, viene eseguito quando viene `TableAdapter.Update()` chiamato il metodo .

Mappare i parametri dalla stored procedure selezionata alle colonne corrispondenti nella tabella dati. Ad esempio, se il stored procedure accetta un parametro denominato che viene passato alla colonna della tabella, impostare la colonna `@CompanyName` di origine del parametro su `CompanyName`  `@CompanyName` `CompanyName` .

> [!NOTE]
> Il stored procedure assegnato al comando SELECT viene eseguito chiamando il metodo dell'oggetto TableAdapter assegnato nel passaggio successivo della procedura guidata. Il metodo predefinito è , quindi il codice usato in genere per `Fill` eseguire la routine SELECT è `TableAdapter.Fill(tableName)` . Se si modifica il nome predefinito da , sostituire con il nome assegnato e sostituire "TableAdapter" con il nome effettivo del `Fill` `Fill` TableAdapter (ad esempio, `CustomersTableAdapter` ).

- La selezione **dell'opzione Crea** metodi per inviare aggiornamenti direttamente al database equivale a impostare `GenerateDBDirectMethods` la proprietà su true. Questa opzione non è disponibile quando l'istruzione SQL originale non fornisce informazioni sufficienti o se la query non è aggiornabile. Questa situazione può verificarsi, ad esempio, nelle **query JOIN** e nelle query che restituiscono un singolo valore (scalare).

Le **opzioni avanzate** della procedura guidata consentono di:

- Generare istruzioni INSERT, UPDATE e DELETE in base all'istruzione SELECT definita nella pagina **Generate SQL statements**
- Usa concorrenza ottimistica
- Specificare se aggiornare la tabella dati dopo l'esecuzione delle istruzioni INSERT e UPDATE

## <a name="configure-a-tableadapters-fill-method"></a>Configurare il metodo Fill di un oggetto TableAdapter

In alcuni casi può essere necessario modificare lo schema della tabella del TableAdapter. A tale scopo, modificare il metodo primario del `Fill` TableAdapter. Gli oggetti TableAdapter vengono creati con un metodo `Fill` primario che definisce lo schema della tabella dati associata. Il metodo primario si basa sulla query o sulla stored procedure immessa al momento della configurazione `Fill` originale del TableAdapter. Si tratta del primo metodo (in primo piano) nella tabella di dati in Progettazione DataSet.

![TableAdapter con più query](../data-tools/media/tableadapter.gif)

Tutte le modifiche apportate al metodo main del TableAdapter vengono riflesse nello `Fill` schema della tabella dati associata. Ad esempio, la rimozione di una colonna dalla query nel metodo main comporta anche la rimozione della `Fill` colonna dalla tabella dati associata. Inoltre, la rimozione della colonna dal metodo main rimuove la colonna da `Fill` eventuali query aggiuntive per tale TableAdapter.

È possibile usare la Configurazione guidata query TableAdapter per creare e modificare query aggiuntive per il TableAdapter. Queste query aggiuntive devono essere conformi allo schema della tabella, a meno che non restituiranno un valore scalare.  Ogni query aggiuntiva ha un nome specificato.

L'esempio seguente illustra come chiamare una query aggiuntiva denominata `FillByCity` :

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Per avviare la Configurazione guidata query TableAdapter con una nuova query

1. Aprire il set di dati in **Progettazione DataSet**.

2. Se si crea una nuova query, trascinare un oggetto  **Query** dalla scheda **DataSet** della Casella degli strumenti in un oggetto oppure selezionare Aggiungi query dal menu di scelta rapida <xref:System.Data.DataTable> del TableAdapter.  È anche possibile trascinare un **oggetto Query** in un'area vuota del **Progettazione DataSet**, che crea un oggetto TableAdapter senza un oggetto <xref:System.Data.DataTable> associato. Queste query possono restituire solo valori singoli (scalari) o eseguire comandi UPDATE, INSERT o DELETE nel database.

3. Nella schermata **Scegli connessione dati** selezionare o creare la connessione che verrà utilizzata dalla query.

    > [!NOTE]
    > Questa schermata viene visualizzata solo quando la finestra di progettazione non è in grado di determinare la connessione appropriata da usare o quando non sono disponibili connessioni.

4. Nella schermata **Scegliere un tipo di comando** selezionare uno dei metodi seguenti per recuperare i dati dal database:

    - **Usare SQL istruzioni** consente di digitare un'SQL per selezionare i dati dal database.

    - **Crea nuovo stored procedure** consente alla procedura guidata di creare un nuovo stored procedure (nel database) in base all'istruzione SELECT specificata.

    - **L'uso di stored procedure** esistenti consente di eseguire un'stored procedure esistente durante l'esecuzione della query.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Per avviare la Configurazione guidata query TableAdapter in una query esistente

- Se si modifica una query TableAdapter esistente, fare clic con il pulsante destro del mouse sulla query e quindi scegliere **Configura** dal menu di scelta rapida.

    > [!NOTE]
    > Facendo clic con il pulsante destro del mouse sulla query principale di un oggetto TableAdapter, il TableAdapter e lo schema vengono <xref:System.Data.DataTable> riconfigurati. Facendo clic con il pulsante destro del mouse su una query aggiuntiva in un oggetto TableAdapter, tuttavia, viene configurata solo la query selezionata. La **Configurazione guidata TableAdapter** riconfigura la definizione del TableAdapter, mentre la Configurazione guidata query **TableAdapter** riconfigura solo la query selezionata.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>Per aggiungere una query globale a un oggetto TableAdapter

- Le query globali SQL query che restituiscono un singolo valore (scalare) o nessun valore. In genere, le funzioni globali eseguono operazioni di database, ad esempio inserimenti, aggiornamenti ed eliminazioni. Aggregano anche informazioni, ad esempio un numero di clienti in una tabella o gli addebiti totali per tutti gli elementi in un ordine specifico.

     Per aggiungere query globali, trascinare un oggetto  **Query** dalla **scheda DataSet** della Casella degli strumenti in un'area vuota della **Progettazione DataSet**.

- Specificare una query che esegue l'attività desiderata, ad esempio `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Trascinando un **oggetto Query** direttamente nel **Progettazione DataSet** viene creato un metodo che restituisce solo un valore scalare (singolo). Mentre la query o stored procedure selezionata potrebbe restituire più di un singolo valore, il metodo creato dalla procedura guidata restituisce solo un singolo valore. Ad esempio, la query potrebbe restituire la prima colonna della prima riga dei dati restituiti.

## <a name="see-also"></a>Vedi anche

- [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)
