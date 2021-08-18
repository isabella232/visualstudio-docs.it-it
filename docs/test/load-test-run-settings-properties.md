---
title: Impostazioni di esecuzione dei test di carico
description: Informazioni su come creare e archiviare più impostazioni di esecuzione per ogni test di carico e quindi selezionare un'impostazione specifica da usare quando si esegue il test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, run settings
ms.assetid: de10dabb-02ed-403b-9e6f-0b735524988c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 1d599f910cc8fc63fe0069ca6447314d2ad9197bc751cf02c08805689717bcf3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440916"
---
# <a name="load-test-run-settings-properties"></a>Proprietà delle impostazioni di esecuzione del test di carico

Le impostazioni di esecuzione di un test di carico determinano una serie di altre impostazioni, tra cui la durata del test, il livello di dettaglio della raccolta dei risultati e gli insiemi di contatori raccolti durante l'esecuzione del test. È possibile creare e archiviare più impostazioni di esecuzione per ogni test di carico e selezionare una determinata impostazioni da usare durante l'esecuzione del test. Quando si crea un test di carico usando la **Creazione guidata test di carico**, al test viene aggiunta un'impostazione esecuzione test iniziale.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Nelle tabelle seguenti vengono descritte le varie proprietà per le impostazioni di esecuzione dei test di carico. È possibile modificare queste proprietà per soddisfare i requisiti specifici del test di carico.

Per altre informazioni, vedere [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md).

## <a name="general-properties"></a>Proprietà generali

|Proprietà|Definizione|
|-|----------------|
|**Descrizione**|Descrizione delle impostazioni di esecuzione.|
|**Numero massimo di errori per tipo**|Numero massimo di errori per tipo da salvare per il test di carico.<br /><br /> L'eventuale aumento di tale numero comporterà un aumento della dimensione e del tempo di elaborazione dei risultati del test di carico.|
|**Numero massimo di URL richiesta restituiti**|Numero massimo di URL di richiesta di test delle prestazioni Web univoci da includere nei risultati del test di carico.<br /><br /> L'eventuale aumento di tale numero comporterà un aumento della dimensione e del tempo di elaborazione dei risultati del test di carico.|
|**Numero massimo di violazioni di soglia**|Numero massimo di violazioni di soglia da salvare per questo test di carico.<br /><br /> L'eventuale aumento di tale numero comporterà un aumento della dimensione e del tempo di elaborazione dei risultati del test di carico.|
|**Esegui unit test in dominio applicazione**|Valore Boolean che determina se ogni assembly di unit test verrà eseguito in un dominio dell'applicazione distinto quando il test di carico contiene unit test. L'impostazione predefinita è True.<br /><br /> Se per la corretta esecuzione degli unit test non è richiesto un file app.config o un dominio applicazione separato, gli unit test potrebbero essere eseguiti più velocemente impostando il valore di questa proprietà su `False`.|
|**Nome**|Nome dell'impostazione di esecuzione come visualizzato nel nodo **Impostazioni esecuzione test** dell'**Editor test di carico**.|
|**Livello di convalida**|Con questo valore viene definito il livello più elevato della regola di convalida che sarà eseguita in un test di carico. Le regole di convalida sono associate alle richieste di test delle prestazioni Web. A ogni regola di convalida è associato un livello di convalida: **Alto**, **Medio** o **Basso**. Questa impostazione di esecuzione del test di carico consente di specificare quali regole di convalida saranno attive durante l'esecuzione del test delle prestazioni Web nel test di carico. Se, ad esempio, questa impostazione di esecuzione è impostata su **Medio**, verranno eseguite tutte le regole di convalida contrassegnate con livello **Medio** o **Basso**.|

## <a name="logging-properties"></a>Proprietà della registrazione

|Proprietà|Definizione|
|-|----------------|
|**Numero massimo di log di test**|Specifica il numero massimo di log di test da salvare per il test di carico. Quando viene raggiunto il valore immesso per il numero massimo di log di test, il test di carico interrompe la raccolta di log. Pertanto, i log verranno raccolti all'inizio del test e non alla fine. L'esecuzione del test di carico continuerà fino al completamento.|
|**Frequenza di salvataggio del log per i test completati**|Specifica la frequenza con la quale viene scritto il log di test. Il numero indica che nel log di test verrà salvato un test ogni numero di test corrispondente al numero immesso. Immettendo, ad esempio, il valore dieci, nel test di log vengono salvati il decimo, il ventesimo, il trentesimo test e così via. Se il valore viene impostato su 0, non verrà salvato alcun log di test.|
|**Salva log su test non superati**|Valore booleano che determina se vengono salvati i log di test in caso di esito negativo di un test in un test di carico. Il valore predefinito è `True`.<br /><br /> Per altre informazioni, vedere [Procedura: Specificare](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md) se gli errori di test vengono salvati nei log di test|

Per altre informazioni, vedere [Modificare le impostazioni di registrazione dei test di carico](../test/modify-load-test-logging-settings.md).

## <a name="results-properties"></a>Proprietà dei risultati

|Proprietà|Definizione|
|-|----------------|
|**Archiviazione digitare**|Modalità di archiviazione dei contatori delle prestazioni ottenuti in un test di carico. descritte di seguito:<br /><br /> -   **Database**: è richiesto un database SQL con un **Archivio risultati test di carico**.<br />-   **Nessuna .**|
|**Dettagli intervallo Archiviazione**|Questa opzione viene usata per determinare i dettagli che verranno archiviati nell'**Archivio risultati test di carico**. Sono disponibili tre valori:<br /><br /> -   **Tutti i singoli dettagli**: consente di raccogliere e archiviare i singoli valori di intervallo per ogni test, transazione e pagina eseguita durante il test di carico nell'**Archivio risultati test di carico**. È necessaria se si intende usare il **Grafico attività utente virtuale** nell'**Analizzatore test di carico**.<br />     Per altre informazioni, vedere [Analizzare l'attività utente virtuale nella visualizzazione Dettagli](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).<br />-   **Nessuno**: Non viene raccolto alcun valore di intervallo singolo. Si tratta del valore predefinito per Visual Studio 2013 Update 4 e versioni successive.<br />-   **Solo statistiche**: consente di raccogliere e archiviare solo le statistiche anziché archiviare i singoli valori di intervallo per ogni test, transazione e pagina eseguita durante il test di carico nell'**Archivio risultati test di carico**.<br /><br /> Per altre informazioni, vedere [Procedura: Specificare](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)la proprietà di archiviazione dei dettagli di intervallo .|

## <a name="sql-tracing-properties"></a>Proprietà della traccia SQL

|Proprietà|Definizione|
|-|----------------|
|**Durata minima operazioni SQL analizzate**|La durata minima di un'operazione SQL da acquisire con la traccia SQL, in millisecondi. Questa opzione consente, ad esempio, di ignorare le operazioni che vengono completate rapidamente se si tenta di individuare le operazioni SQL che risultano lente sotto carico.|
|**Stringa di connessione traccia SQL**|La stringa di connessione usata per accedere al database di cui eseguire la traccia.|
|**Directory traccia SQL**|L'ubicazione in cui viene inserito il file Traccia SQL al termine della traccia. Questa directory deve avere le autorizzazioni di scrittura per SQL Server e le autorizzazioni di lettura per il controller.|
|**Traccia SQL attivata**|Consente di attivare la traccia delle operazioni SQL. Il valore predefinito è `False`.|

## <a name="test-iterations-properties"></a>Proprietà delle iterazioni test

|Proprietà|Definizione|
|-|----------------|
|**Iterazioni di test**|Specifica il numero totale di test singoli da eseguire prima che il test di carico sia completato. Questa proprietà si applica solo quando la proprietà "usa iterazioni test" è `True`.|
|**Utilizza iterazioni test**|Se la proprietà "Utilizza iterazioni test" è `True`, il test di carico viene eseguito finché il numero di test singoli completati nell'ambito del test di carico non raggiunge il valore specificato dalla proprietà "Iterazioni test". In questo caso, le impostazioni basate sul tempo, ossia "Durata riscaldamento", "Durata esecuzione" e "Durata raffreddamento", verranno ignorate. Se "Utilizza iterazioni test" è `False`, verranno applicate tutte le impostazioni basate sul tempo e la proprietà "Iterazioni test" verrà ignorata.|

Per altre informazioni, vedere Procedura: Specificare il numero di [iterazioni di test in un'impostazione di esecuzione](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="timing-properties"></a>Proprietà dell'intervallo

|Proprietà|Definizione|
|-|----------------|
|**Durata raffreddamento**|Durata del periodo di raffreddamento per il test, espressa nel formato hh:mm:ss. È possibile che singoli test di un test di carico siano ancora in esecuzione al termine del test di carico. Durante il periodo di raffreddamento, viene consentita la continuazione di tali test fino al relativo completamento o al termine del periodo di raffreddamento. Per impostazione predefinita, il periodo di raffreddamento è disattivato e i singoli test vengono terminati al completamento del test di carico in base all'impostazione "Durata esecuzione".|
|**Durata esecuzione**|La durata del test, in formato hh:mm:ss.|
|**Frequenza di campionamento**|L'intervallo per l'acquisizione dei valori dei contatori delle prestazioni, in formato hh:mm:ss.<br /><br /> Per altre informazioni, vedere [Procedura: Specificare la frequenza di campionamento.](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Durata riscaldamento**|Il periodo compreso tra l'inizio del test e l'inizio della registrazione dei campioni di dati, in formato hh:mm:ss. Questo valore viene spesso usato per consentire a utenti virtuali di carico di raggiungere determinati livelli di carico prima di registrare i valori campione. I valori campione acquisiti prima della fine del periodo di riscaldamento vengono visualizzati in **Analizzatore test di carico**.|

## <a name="webtest-connections-properties"></a>Proprietà delle connessioni WebTest

|Proprietà|Definizione|
|-|----------------|
|**Modello di connessione WebTest**|Controlla l'uso delle connessioni dall'agente del test di carico al server Web per i test delle prestazioni Web inclusi in un test di carico. Per il modello di connessione del test delle prestazioni Web sono disponibili tre opzioni:<br /><br /> -   Il modello **Connessione per utente** simula il comportamento di un utente che usa un browser reale. Quando viene simulato Internet Explorer 6 o Internet Explorer 7, ogni utente virtuale che esegue un test delle prestazioni Web usa una o due connessioni dedicate al server Web. La prima connessione viene stabilita quando viene emessa la prima richiesta nel test delle prestazioni Web. Una seconda connessione può essere usata quando una pagina contiene più di una richiesta dipendente. Queste richieste vengono emesse in parallelo usando le due connessioni. Queste connessioni vengono riutilizzate per le richieste successive nel test delle prestazioni Web. Al termine del test delle prestazioni Web, le connessioni vengono chiuse. Uno svantaggio di questo modello è che il numero di connessioni aperte nel computer agente può essere elevato (fino a due volte il carico utente). Pertanto, le risorse richieste per supportare questo numero elevato di connessioni potrebbero limitare il carico utente che può essere determinato da un singolo agente di test di carico. Quando viene simulato Internet Explorer 8, sono supportate sei connessioni simultanee.<br />- Il **modello Pool di** connessioni conserva le risorse nell'agente del test di carico condividendo le connessioni al server Web tra più utenti di test delle prestazioni Web virtuali. Se il carico utente è maggiore delle dimensioni del pool di connessioni, i test delle prestazioni Web eseguiti da utenti virtuali diversi condivideranno una connessione. Questo significa che, quando la connessione è in uso in un altro test delle prestazioni Web, potrebbe essere necessario un periodo di attesa prima che il test emetta una richiesta. Il tempo medio di attesa di un test delle prestazioni Web prima di inviare una richiesta viene monitorato dalla funzionalità relativa al tempo medio di attesa connessione del contatore delle prestazioni del test di carico. Questo valore deve essere inferiore al tempo di risposta medio per una pagina. In caso contrario, la dimensione del pool di connessioni è probabilmente insufficiente.<br />-   Il modello **Connessione per iterazione test** specifica l'uso di connessioni dedicate per ogni iterazione del test.|
|**Dimensione pool di connessioni WebTest**|Consente di specificare il numero massimo di connessioni da stabilire tra l'agente del test di carico e il server Web. Si applica solo al modello **Pool di connessioni**.|

## <a name="change-run-setting-properties"></a>Modificare le proprietà delle impostazioni di esecuzione

È possibile aggiungere altre impostazioni di esecuzione al test di carico con impostazioni di proprietà differenti, per poter eseguire il test di carico con condizioni diverse. Ad esempio, è possibile aggiungere una nuova impostazione test e usare una frequenza di campionamento diversa o specificare una durata dell'esecuzione più lunga. È possibile usare una sola impostazione di esecuzione test per volta ed è necessario specificare quale impostazione di esecuzione test usare contrassegnandola come attiva. Per un esempio, vedere [Procedura: Selezionare l'impostazione esecuzione test attiva per un test di carico.](../test/how-to-select-the-active-run-setting-for-a-load-test.md)

Per modificare le impostazioni di esecuzione test:

1. Aprire un test di carico.

2. Espandere la cartella **Impostazioni di esecuzione**.

3. Scegliere il nodo **Impostazioni esecuzione test**.

4. Scegliere **Finestra Proprietà** dal menu **Visualizza**.

     Verrà visualizzata la **Finestra Proprietà** con le proprietà relative all'impostazione di esecuzione selezionata.

5. Usare la **Finestra Proprietà** per modificare le impostazioni di esecuzione. Modificare, ad esempio, la durata dell'esecuzione in **00:05:00** per eseguire il test per cinque minuti.

    > [!NOTE]
    > Per un elenco completo delle proprietà delle impostazioni esecuzione test e delle relative descrizioni, vedere Proprietà [delle impostazioni esecuzione test di carico.](../test/load-test-run-settings-properties.md)

6. Dopo aver terminato le modifiche alle proprietà, salvare il test di carico. Nel menu **File** scegliere **Salva**.

> [!NOTE]
> Anche i mapping insiemi di contatori fanno parte delle impostazioni di esecuzione. Per altre informazioni, vedere [Specificare gli insiemi di contatori e le regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
