---
title: Creare un'impostazione di test per un test di carico distribuito
description: Informazioni su come configurare le impostazioni di test per i test di carico in modo da poter distribuire tali test tra più computer usando agenti di test e controller di test.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 7e08163be95d2249b091ce40072d54111e35ef2b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033278"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Procedura: Creare un file di impostazioni test per un test di carico distribuito

Configurare le *impostazioni test* per i test di carico per consentirne la distribuzione tra più computer con agenti di test e test controller. È anche possibile configurare le impostazioni test per l'uso degli *adattatori dati di diagnostica* che specificano i tipi di dati da raccogliere o il funzionamento dei computer di test quando si eseguono i test di carico da Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Ad esempio, è possibile utilizzare l'adattatore dati di diagnostica del profiler di ASP.NET per raccogliere i dati suddivisi delle prestazioni del codice. È inoltre possibile utilizzare gli adattatori dati di diagnostica per simulare potenziali colli di bottiglia nel computer di test o per ridurre la memoria di sistema disponibile.

Le impostazioni test per Visual Studio vengono archiviate in un file. Le impostazioni test definiscono le seguenti informazioni su ogni ruolo:

- Il set di ruoli necessario per l'applicazione sottoposta a test

- Il ruolo da utilizzare per eseguire i test

- Gli adattatori dati di diagnostica da utilizzare per ciascun ruolo

Quando si eseguono i test, si selezionano le impostazioni di test da utilizzare come impostazioni attive a seconda delle esigenze correlate allo specifico test da eseguire. Il file delle impostazioni di test è archiviato come parte della soluzione. Il nome file ha l'estensione *testsettings*.

Quando si aggiunge un progetto di test di carico e prestazioni Web a una soluzione, viene creato un file *Default.testsettings.* Il file viene aggiunto automaticamente alla soluzione nella cartella **Elementi di soluzione**. Questo file esegue i test in locale senza adattatori dati di diagnostica. È possibile aggiungere un altro file con estensione *testsettings* o modificare un file con estensione *testsettings* per specificare gli adattatori dati di diagnostica e i test controller.

Il controller di test disporrà di agenti che possono essere usati per ogni ruolo nelle impostazioni di test. Per altre informazioni sui test controller e gli agenti di test, vedere [Gestire test controller e agenti di test con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Eseguire la procedura seguente per creare e rimuovere impostazioni di test nella soluzione per i test di carico che si intende eseguire da Visual Studio.

## <a name="create-a-test-settings-file"></a>Creare un file di impostazioni test

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Elementi di soluzione**, scegliere **Aggiungi** e quindi **nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro **Modelli installati** scegliere **Impostazioni test**.

3. (Facoltativo) Nella casella **Nome** cambiare il nome del file delle impostazioni test.

4. Scegliere **Aggiungi**.

     Il nuovo file delle impostazioni di test **viene visualizzato Esplora soluzioni**, nella cartella Elementi **di** soluzione.

5. Verrà visualizzata la finestra di dialogo **Impostazioni test**. È selezionata la pagina **Generale**.

     È quindi possibile modificare e salvare i valori delle impostazioni di test.

6. In **Nome** digitare il nome per le impostazioni di test.

7. (Facoltativo) In **Descrizione** digitare una descrizione per l'impostazione test in modo da indicarne la funzione agli altri membri del team.

8. (Facoltativo) Per selezionare lo schema di denominazione predefinito per le esecuzioni dei test, selezionare **Schema di denominazione predefinito**. Per definire uno schema di denominazione personalizzato, selezionare **Schema definito dall'utente**, quindi digitare il testo desiderato in **Testo prefisso**. Per aggiungere la data e l'ora al nome dell'esecuzione del test, selezionare **Aggiungi indicatore data e ora**.

9. Scegliere **Ruoli**.

     Verrà visualizzata la pagina **Ruoli**.

     ![Ruolo impostazioni test](../test/media/load_testtestrole.png)

10. Per eseguire i test in modalità remota o per eseguire i test e raccogliere dati in modalità remota, usare l'elenco a discesa **Metodo di esecuzione dei test** e selezionare **Esecuzione remota**.

11. Usare l'elenco a discesa **Controller** per selezionare un test controller per gli agenti di test da **Controller** che verrà usato per eseguire i test o raccogliere dati.

    > [!NOTE]
    > Se si aggiunge un controller per la prima volta, nell'elenco a discesa non saranno presenti controller. L'elenco viene popolato da controller precedenti specificati in altre impostazioni di test. È necessario digitare il nome del controller nella casella, ad esempio **TestControllerMachine1**.

12. Per aggiungere i ruoli che si vuole usare per eseguire i test e raccogliere dati, in **Ruoli** scegliere **Aggiungi**.

13. Digitare un nome per il ruolo nella colonna **Nome**. Ad esempio, il ruolo potrebbe essere "Server Web".

14. Ripetere i passaggi 12 e 13 per aggiungere tutti i ruoli necessari.

     Per ogni ruolo viene utilizzato un agente di test gestito dal controller di test.

15. Selezionare il ruolo per il quale si vuole eseguire i test, quindi scegliere **Imposta come ruolo per l'esecuzione di test**.

    > [!IMPORTANT]
    > Gli altri ruoli creati e definiti non consentiranno l'esecuzione di test, ma verranno usati solo per raccogliere dati in base agli adattatori dati e agli adattatori di diagnostica specificati per i ruoli nella pagina **Dati e diagnostica**.

16. Per limitare gli agenti che possono essere usati per  un ruolo, selezionare il ruolo e quindi scegliere Aggiungi nella barra degli strumenti in **Attributi agente per il ruolo selezionato.**

     Viene visualizzata la finestra di dialogo **Regola di selezione agenti**.

     Digitare il nome in **Nome attributo** e il valore in **Valore attributo**, quindi scegliere **OK**. Aggiungere tutti gli attributi necessari.

     Ad esempio, è possibile aggiungere un attributo denominato "RAM > 16 GB" con un valore "True" o "False" per filtrare i computer di agenti di test con più di 16 GB di memoria. Per applicare lo stesso attributo a uno o più agenti di test, viene utilizzata la finestra di dialogo **Gestisci controller di test**. Per altre informazioni, vedere [Gestire test controller e agenti di test con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Scegliere **Dati e diagnostica**.

     Verrà visualizzata la pagina **Dati e diagnostica**.

     ![Test dei dati delle impostazioni e diagnostica](../test/media/load_testtest.png)

18. Nella pagina **Dati e diagnostica** viene definita l'azione eseguita dal ruolo selezionando gli *adattatori dati di diagnostica* che verranno usati dal ruolo per raccogliere dati. Pertanto, se per il ruolo sono abilitati uno o più adattatori dati e adattatori diagnostici, tramite il controller di test verrà selezionato un computer dell'agente di test disponibile per raccogliere dati per gli adattatori dati e gli adattatori diagnostici specificati in base agli attributi definiti per il ruolo. Per selezionare gli adattatori dati e gli adattatori diagnostici che si vuole raccogliere per ogni ruolo, selezionare il ruolo. Per ogni ruolo, selezionare gli adattatori dati di diagnostica in base alle esigenze dei test. Per configurare ogni adattatore dati di diagnostica selezionato per ogni ruolo, scegliere **Configura**.

     **Esempio di ruoli e di adattatori dati di diagnostica:**

     Ad esempio, è possibile creare un ruolo client denominato "Client desktop" con un attributo "Utilizza SQL" impostato su "True" e un ruolo server denominato "SQL Server" con un attributo impostato su "RAM > 16 GB". Se si specifica che i test verranno eseguiti dal "Client desktop" scegliendo **Imposta come ruolo per l'esecuzione di test** nella pagina **Ruoli**, il test controller seleziona i computer con agenti di test che includono l'attributo "Utilizza SQL" impostato su "True" su cui eseguire i test. Tramite il test controller verranno selezionati inoltre i computer SQL Server con agenti di test contenenti l'attributo "RAM > 16 GB" solo per raccogliere i dati definiti dagli adattatori dati e dagli adattatori diagnostici inclusi nel ruolo. Anche tramite l'agente di test "Client desktop" è possibile raccogliere dati per i computer sui quali viene eseguito, ma solo se si selezionano anche gli adattatori dati e gli adattatori diagnostici per tale ruolo.

     Per informazioni dettagliate su ogni adattatore dati di diagnostica e su come configurarlo, è possibile visualizzare l'argomento associato nella tabella seguente.

     Per altre informazioni sugli adattatori dati di diagnostica, vedere [Raccogliere informazioni di diagnostica usando le impostazioni di test.](../test/collect-diagnostic-information-using-test-settings.md)

     **Adattatori dati di diagnostica per test di carico**

    |Adattatore dati di diagnostica|Utilizzo nei test di carico|Argomento associato|
    |-|-------------------------|-|
    |**Proxy client ASP.NET per IntelliTrace e impatto test:** questo proxy consente di raccogliere informazioni sulle chiamate http da un client a un server Web per gli adattatori dati di diagnostica di IntelliTrace e impatto test.|![Icona Informazioni](../test/media/vc364f4.gif)<br /><br /> A meno che ci sia una specifica esigenza di raccogliere informazioni sul sistema per i computer degli agenti di test, non includere questo adattatore. **Attenzione:** non si consiglia l'utilizzo dell'adattatore IntelliTrace nei test di carico a causa dei problemi che si verificano per la grande quantità di dati raccolti. <br /><br /> I dati dell'impatto sui test non vengono raccolti tramite test di carico.||
    |**IntelliTrace:** è possibile configurare informazioni specifiche sulla traccia diagnostica archiviate in un file di log. Un file di log ha estensione *tdlog*. Quando si esegue il test e un passo del test non riesce, è possibile creare un bug. Il file di log che contiene la traccia diagnostica viene associato automaticamente al bug. I dati raccolti nel file di log aumentano la produttività di debug riducendo il tempo necessario per riprodurre e diagnosticare un errore nel codice. Da questo file di log è possibile ricreare la sessione locale in un altro computer. In questo modo si riduce il rischio che non sia possibile riprodurre un bug.<br /><br /> Per altre informazioni, vedere [Raccogliere dati IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Icona Importante](../test/media/vc364f3.gif)<br /><br /> Non si consiglia l'utilizzo dell'adattatore IntelliTrace nei test di carico a causa dei problemi che si verificano per la grande quantità di dati raccolti e registrati. È opportuno tentare di utilizzare l'adattatore IntelliTrace solo in test di carico che non hanno lunga esecuzione e non utilizzano molti agenti di test.|[Procedura: Raccogliere dati di IntelliTrace per agevolare il debug di problemi complessi](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**ASP.NET Profiler:** È possibile creare un'impostazione di test che includa ASP.NET di profilatura, che raccoglie i dati sulle prestazioni ASP.NET applicazioni Web.|L'adattatore dati di diagnostica del profiler ASP.NET profila il processo di Internet Information Services (IIS), pertanto non funzionerà con un server web di sviluppo. Per profilare il sito web nel test di carico, è necessario installare un agente di test nel computer sul quale IIS è in esecuzione. L'agente di test non genererà carico, ma sarà un agente di sola raccolta. Per altre informazioni, vedere [Installare e configurare agenti di test](../test/lab-management/install-configure-test-agents.md).|[Procedura: Configurare un profiler ASP.NET per i test di carico usando le impostazioni test](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Log eventi:** è possibile configurare un'impostazione test in modo da includere la raccolta del log eventi, che verrà inserita nei risultati dei test.||[Procedura: Configurare la raccolta di log eventi usando le impostazioni test](/previous-versions/dd504816(v=vs.110))|
    |**Emulazione di rete:** è possibile specificare che si vuole aggiungere un carico di rete artificiale al test usando un'impostazione test. L'emulazione di rete influisce sulla comunicazione da e verso il computer emulando una determinata velocità della connessione di rete, ad esempio di una connessione remota. **Nota:** non è possibile usare l'emulazione di rete per aumentare la velocità della connessione di rete.|L'adattatore di emulazione di rete viene ignorato dai test di carico. Al contrario, i test di carico usano le impostazioni specificate nella combinazione di reti dello scenario dei test di carico.<br /><br /> Per altre informazioni, vedere [Specificare i tipi di rete virtuale](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Informazioni di sistema:** è possibile configurare un'impostazione test per includere le informazioni di sistema dei computer su cui viene eseguito l'agente di raccolta di dati e diagnostica delle informazioni di sistema. Le informazioni di sistema sono specificate nei risultati del test tramite un'impostazione di test.|![Icona di informazioni](../test/media/vc364f4.gif)<br /><br /> È possibile raccogliere informazioni di sistema sia dagli agenti di carico che dal sistema sottoposto a test.|Per raccogliere queste informazioni, non è necessaria alcuna configurazione.|
    |**Impatto test:** è possibile raccogliere informazioni sui metodi del codice dell'applicazione usati durante l'esecuzione di un test case. Queste informazioni possono essere utilizzate insieme a quelle relative alle modifiche apportate al codice dell'applicazione dagli sviluppatori per individuare i test interessati da tali modifiche di sviluppo.|I dati dell'impatto sui test non vengono raccolti con i test di carico.||
    |**Videoregistratore:** è possibile creare una registrazione video della sessione desktop durante l'esecuzione di un test automatizzato. La registrazione può essere utile per visualizzare le azioni dell'utente per un test codificato dell'interfaccia utente. Il video può consentire ad altri membri del team di isolare i problemi dell'applicazione difficili da riprodurre. **Nota:** durante l'esecuzione di test in modalità remota, il videoregistratore non funzionerà a meno che l'agente non venga eseguito in modalità processo interattivo.|![Icona importante ](../test/media/vc364f3.gif) **Avviso: non**  è consigliabile usare l'adattatore Video Recorder per i test di carico.|[Procedura: Includere le registrazioni dello schermo e della voce durante i test usando le impostazioni test](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Scegliere **Distribuzione**.

     Viene visualizzata la pagina **Distribuzione**.

20. Per creare una directory distinta per la distribuzione ogni volta che si eseguono i test, selezionare **Abilita distribuzione**.

    > [!NOTE]
    > Se si seleziona questa opzione, sarà possibile continuare a compilare l'applicazione durante l'esecuzione dei test.

21. Per aggiungere un file alla directory usata per l'esecuzione dei test, scegliere **Aggiungi file**, quindi selezionare il file che si vuole aggiungere.

    > [!NOTE]
    > Quando si eseguono i test di carico, gli assembly di plug-in, i file di dati e i file caricati vengono distribuiti automaticamente.

22. Per aggiungere una directory alla directory usata per l'esecuzione dei test, scegliere **Aggiungi directory**, quindi selezionare la directory che si vuole aggiungere.

23. Per eseguire script prima e dopo i test, scegliere **Script di installazione e pulizia**.

     Viene visualizzata la pagina **Script di installazione e pulizia**.

    1. Digitare il percorso del file di script in **Script di installazione** oppure fare clic sui puntini di sospensione (**…**) per individuare lo script.

    2. Digitare il percorso del file di script in **Script di pulizia** oppure fare clic sui puntini di sospensione (**…**) per individuare lo script.

24. Per eseguire i test usando un host diverso, scegliere **Host**.

    1. In **Tipo host** verificare che **Predefinito** sia selezionato.

        > [!NOTE]
        > Il **Tipo host****ASP.NET** non è supportato nei test di carico.

    2. Usare l'elenco a discesa **Esegui test in un processo a 32 bit o a 64 bit** per scegliere se i test delle prestazioni Web e gli unit test nel test di carico devono essere eseguiti come processi a 32 bit o a 64 bit.

        > [!NOTE]
        > Per la massima flessibilità, è consigliabile compilare i progetti di test di carico e prestazioni Web usando la **configurazione Qualsiasi CPU.** È quindi possibile effettuare l'esecuzione sia su agenti a 32 bit che a 64 bit. La compilazione di progetti di test di carico e prestazioni Web con la configurazione a **64 bit** non offre alcun vantaggio.

25. (Facoltativo) Per limitare la durata di ogni esecuzione di test e dei singoli test, scegliere **Timeout test**.

    1. Per interrompere un'esecuzione di test quando viene superato un limite di tempo, selezionare **Interrompi una esecuzione dei test se il tempo totale supera**, quindi digitare un valore per il limite.

    2. Per generare un errore in un singolo test quando viene superato un limite di tempo, selezionare **Contrassegna singolo test come non superato se il tempo di esecuzione è maggiore di**, quindi digitare un valore per il limite.

26. Ignorare **Unit test**. I test di carico non utilizzano queste impostazioni.

27. Ignorare **Test Web**. I test di carico non utilizzano queste impostazioni.

28. Per salvare le impostazioni test, scegliere **Salva con nome**. Digitare il nome di file desiderato in **Nome oggetto**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Rimuovere un file di impostazioni test dalla soluzione

Nella cartella **Elementi di soluzione** in **Esplora soluzioni** fare clic con il pulsante destro del mouse su impostazioni test da rimuovere e quindi **scegliere Rimuovi.**

Il file delle impostazioni di test verrà rimosso dalla soluzione.

## <a name="see-also"></a>Vedi anche

- [Test controller e agenti di test](configure-test-agents-and-controllers-for-load-tests.md)
- [Raccogliere dati di diagnostica usando impostazioni test](../test/collect-diagnostic-information-using-test-settings.md)