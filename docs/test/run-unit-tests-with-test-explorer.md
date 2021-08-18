---
title: Eseguire unit test con Esplora test
description: Informazioni sull'esecuzione di test con Esplora test in Visual Studio. Questo argomento illustra come abilitare le esecuzioni test automatiche dopo la compilazione, visualizzare i risultati dei test, raggruppare e filtrare l'elenco di test, creare playlist e usare i collegamenti ai test.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 9c9f31d17a4a1453020f5e18b4877beb7344d50d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100504"
---
# <a name="run-unit-tests-with-test-explorer"></a>Eseguire unit test con Esplora test

Usare Esplora test per eseguire unit test da Visual Studio o da progetti di unit test di terze parti. È anche possibile usare Esplora test per raggruppare i test in categorie, filtrare l'elenco dei test e creare, salvare ed eseguire playlist di test. È anche possibile analizzare i code coverage ed [eseguire il debug di unit test](../test/debug-unit-tests-with-test-explorer.md).

**Esplora test** può eseguire test da più progetti di test in una soluzione e da classi di test appartenenti a progetti di codice di produzione. I progetti di test possono usare framework di unit test diversi. Se il codice sottoposto a test è scritto per .NET, il progetto di test può essere scritto in qualsiasi linguaggio destinato anche a .NET, indipendentemente dal linguaggio del codice di destinazione. I progetti in codice C/C++ nativo devono essere testati tramite un framework di unit test C++.

## <a name="build-your-test-project"></a>Compilare il progetto di test

Se non è già stato configurato un progetto di test nella soluzione Visual Studio, è necessario creare e compilare un progetto di test.

- [Introduzione all'unit test (.NET)](../test/getting-started-with-unit-testing.md)
- [Scrivere unit test per C/C++](writing-unit-tests-for-c-cpp.md)

Visual Studio include i framework di unit test Microsoft sia per il codice gestito sia per quello nativo. Esplora test può tuttavia eseguire anche qualsiasi framework di unit test in cui sia implementato un adattatore di Esplora test. Per altre informazioni sull'installazione di framework di unit test di terze parti, vedere [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md).

## <a name="run-tests-in-test-explorer"></a>Eseguire test in Esplora test

Quando si compila il progetto di test, i test vengono visualizzati in Esplora test. Se Esplora test non  è visibile, scegliere Test dal menu Visual Studio, scegliere **Windows** e quindi scegliere **Esplora** test (o premere **CTRL**  +  **E**, **T**).

::: moniker range="vs-2017"
![Esplora unit test](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Esplora test](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Quando si eseguono, si scrivono e si rieseguono i test, Esplora test mostra i risultati nei gruppi predefiniti **Test non superati**, **Test superati**, **Test ignorati** e **Test non eseguiti**. È possibile modificare la modalità con cui Esplora test raggruppa i test.
::: moniker-end
::: moniker range=">=vs-2019"
Quando si eseguono, scrivono e rieseguono i test, Esplora test visualizza i risultati in un raggruppamento predefinito di **Progetto**, **Spazio dei nomi** e **Classe**. È possibile cambiare il modo in cui Esplora test raggruppa i test.
::: moniker-end

È possibile eseguire molte delle operazioni di ricerca, organizzazione ed esecuzione dei test dalla barra degli strumenti di **Esplora test**.

::: moniker range="vs-2017"
![Eseguire test dalla barra degli strumenti di Esplora test](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eseguire test dalla barra degli strumenti di Esplora test](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Esecuzione dei test

::: moniker range="vs-2017"
È possibile eseguire tutti i test nella soluzione, tutti i test in un gruppo o un set di test selezionati. Eseguire una delle operazioni seguenti:

- Per eseguire tutti i test in una soluzione, scegliere **Esegui tutto** oppure premere **CTRL** + **R**, **V**.

- Per eseguire tutti i test in un gruppo predefinito, scegliere **Esegui** e quindi scegliere il gruppo dal menu.

- Selezionare i singoli test da eseguire, aprire il menu di scelta rapida per un test selezionato e quindi scegliere **Esegui** test selezionati oppure premere **CTRL** + **R**, **T**.

- Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione parallela dei test con l'interruttore ![Screenshot dell'interruttore Esecuzione test in parallelo sulla barra degli strumenti Visual Studio Esplora test. Quando questo pulsante è selezionato, i test verranno eseguiti in parallelo.](../test/media/ute_parallelicon-small.png) sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.

Mentre il test viene eseguito, la barra **Superato/Non superato** nella parte superiore della finestra **Esplora test** visualizza un'animazione. Al termine dell'esecuzione del test, la barra **Superato/Non superato** diventa verde se tutti i test sono stati superati o rossa se un test non è stato superato.
::: moniker-end
::: moniker range=">=vs-2019"
È possibile eseguire tutti i test nella soluzione, tutti i test in un gruppo o un set di test selezionati. Eseguire una delle operazioni seguenti:

- Per eseguire tutti i test in una soluzione, scegliere **l'icona** Esegui tutto oppure premere **CTRL** + **R**, **V**.

- Per eseguire tutti i test in un gruppo predefinito, scegliere **Esegui** e quindi scegliere il gruppo dal menu.

- Selezionare i singoli test da eseguire, aprire il menu di scelta rapida per un test selezionato e quindi scegliere **Esegui** test selezionati oppure premere **CTRL** + **R**, **T**.

- Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione parallela dei test nel menu Impostazioni sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Eseguire test dopo ogni compilazione
::: moniker range="vs-2017"
|Pulsante|Descrizione|
|-|-|
|![Esecuzione dopo la compilazione](../test/media/ute_runafterbuild_btn.png)|Per eseguire gli unit test dopo ogni compilazione locale, scegliere **Test** dal menu standard e quindi scegliere **Esegui test dopo compilazione** sulla barra degli strumenti di **Esplora test**.|

> [!NOTE]
> Per eseguire unit test dopo ogni compilazione è necessario Visual Studio 2017 Enterprise o Visual Studio 2019. In Visual Studio 2019 la funzionalità è inclusa nelle versioni Community, Professional ed Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Per eseguire gli unit test dopo ogni compilazione locale, aprire l'icona Impostazioni sulla barra degli strumenti di Esplora test e selezionare **Esegui test dopo compilazione**.
::: moniker-end

## <a name="view-test-results"></a>Visualizzare i risultati dei test

Quando si eseguono, si scrivono e si rieseguono i test, Esplora test mostra i risultati nei gruppi **Test non superati**, **Test superati**, **Test ignorati** e **Test non eseguiti**. Il riquadro dei dettagli nella parte inferiore o laterale della finestra Esplora test mostra un riepilogo dell'esecuzione dei test.

### <a name="view-test-details"></a>Visualizzare i dettagli dei test

Per visualizzare i dettagli di un singolo test, selezionare il test.

::: moniker range="vs-2017"
![Dettagli sull'esecuzione dei test](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Dettagli sull'esecuzione dei test](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Il riquadro dei dettagli del test mostra le informazioni seguenti:

- Nome del file di origine e numero di riga del metodo di test.

- Stato del test.

- Tempo impiegato per l'esecuzione del metodo di test.

Se il test non viene superato, il riquadro dei dettagli mostra anche le informazioni seguenti:

- Messaggio restituito dal framework di unit test per il test.

- Analisi dello stack al momento del mancato superamento del test.

### <a name="view-the-source-code-of-a-test-method"></a>Visualizzare il codice sorgente di un metodo di test

Per visualizzare il codice sorgente per un metodo di test nell'editor di Visual Studio, selezionare il test e quindi scegliere Apri test dal menu di scelta rapida (o premere **F12).** 

## <a name="group-and-filter-the-test-list"></a>Raggruppare e filtrare l'elenco dei test

Esplora test consente di raggruppare i test in categorie predefinite. La maggior parte dei framework di unit test eseguiti in Esplora Test consente di definire categorie personalizzate e coppie categoria/valore per raggruppare i test. È anche possibile filtrare l'elenco dei test in base a stringhe corrispondenti nelle proprietà dei test.

### <a name="group-tests-in-the-test-list"></a>Raggruppare i test nell'elenco di test

::: moniker range="vs-2017"
Per modificare la modalità di organizzazione dei test, scegliere la freccia rivolta verso il basso accanto al pulsante **Raggruppamento**![Pulsante Raggruppamento di Esplora test](../test/media/ute_groupby_btn.png) e selezionare un nuovo criterio di raggruppamento.

![Raggruppare i test per categoria in Esplora test](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Esplora test consente di raggruppare i test in una gerarchia. Il raggruppamento predefinito della gerarchia è **Progetto**, **Spazio dei nomi** e quindi **Classe**. Per cambiare il modo in cui sono organizzati i test, scegliere il pulsante **Raggruppa per**![Pulsante Raggruppa per di Esplora test](../test/media/ute_groupby_btn.png) e selezionare un nuovo criterio di raggruppamento.

![Raggruppare i test per categoria in Esplora test](../test/media/vs-2019/test-explorer-groupby-162.png)

È possibile definire i propri livelli della gerarchia e raggruppare in base a **Stato** e quindi a **Classe**, ad esempio, selezionando le opzioni di Raggruppa per nell'ordine preferito.

![Screenshot dell'Visual Studio Esplora test che mostra una gerarchia di test in un riquadro e il menu Raggruppa per nell'altro con le opzioni Classe e Stato selezionate.](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Gruppi di Esplora test

::: moniker range="vs-2017"
|Gruppo|Descrizione|
|-|-----------------|
|**Duration**|Raggruppa i test in base al tempo di esecuzione: **Veloce**, **Medio** e **Lento**.|
|**Risultato**|Raggruppa i test in base ai risultati di esecuzione: **Test non superati**, **Test ignorati**, **Test superati**.|
|**Tratti**|Raggruppa i test in base a coppie categoria/valore definite. La sintassi per specificare i valori e le categorie dei tratti è definita dal framework di unit test.|
|**Progetto**|Raggruppa i test in base al nome dei progetti.|
::: moniker-end
::: moniker range=">=vs-2019"
|Gruppo|Descrizione|
|-|-----------------|
|**Duration**|Raggruppa i test in base al tempo di esecuzione: **Veloce,** **Medio** e **Lento.**|
|**State**|Raggruppa i test in base ai risultati **dell'esecuzione: test non superati,** test **ignorati,** **test superati,** **non eseguiti**|
|**Framework di destinazione** | Raggruppa i test in base al framework di destinazione dei progetti |
|**Namespace**|Raggruppa i test in base allo spazio dei nomi contenitore.|
|**Progetto**|Raggruppa i test in base al progetto contenitore.|
|**Classe**|Raggruppa i test in base alla classe contenitore.|
::: moniker-end

### <a name="traits"></a>Tratti

Una tratto è in genere una coppia nome/valore di una categoria, ma può anche essere una singola categoria. I tratti possono essere assegnati ai metodi identificati come metodi di test dal framework di unit test. Un framework di unit test può definire le categorie dei tratti. È possibile aggiungere valori alle categorie dei tratti per definire coppie nome/valore personalizzate per le categorie. La sintassi per specificare i valori e le categorie dei tratti è definita dal framework di unit test.

**Tratti nel framework di unit test Microsoft per il codice gestito**

Nel framework di unit test Microsoft per le app gestite, una coppia nome/valore di un tratto viene definita in un attributo  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . Il framework di test contiene anche i tratti predefiniti seguenti:

|Caratteristica|Descrizione|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|La categoria Owner è definita dal framework di unit test e richiede di specificare un valore di stringa relativo al proprietario.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|La categoria Priority è definita dal framework di unit test e richiede di specificare un valore integer relativo alla priorità.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|L'attributo TestCategory consente di specificare la categoria di un unit test.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|L'attributo TestProperty consente di definire una coppia categoria/valore di un tratto.|


**Tratti nel framework di unit test Microsoft per C++**

Vedere [Come usare il framework di testing unità Microsoft per C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Creare playlist personalizzate

::: moniker range="vs-2017"
È possibile creare e salvare un elenco di test da eseguire o visualizzare come gruppo. Quando si seleziona una playlist, i test inclusi nell'elenco vengono visualizzati in Esplora test. È possibile aggiungere un test a più playlist e tutti i test del progetto saranno disponibili quando si sceglie la playlist predefinita **Tutti i test** .

![Scegliere una playlist](../test/media/ute_playlist.png)

**Per creare una playlist**, scegliere uno o più test in Esplora Test. Scegliere Aggiungi alla playlist   >  **NewPlaylist** dal menu di scelta rapida. Salvare il file con il nome e il percorso specificati nella finestra di dialogo **Crea nuova playlist** .

**Per aggiungere test a una playlist**, scegliere uno o più test in Esplora Test. Scegliere **Aggiungi a playlist** dal menu di scelta rapida e quindi scegliere la playlist a cui aggiungere i test.

Per aprire una  **playlist,** scegliere Prova playlist dal menu Visual Studio e scegliere dall'elenco di playlist usate di recente oppure scegliere Apri playlist per specificare il nome e il percorso della >  playlist. 

Se i singoli test non hanno dipendenze che ne impediscono l'esecuzione in qualsiasi ordine, attivare l'esecuzione parallela dei test con l'interruttore ![Screenshot dell'interruttore Esecuzione test in parallelo sulla barra degli strumenti Visual Studio Esplora test.](../test/media/ute_parallelicon-small.png) sulla barra degli strumenti. Questo può ridurre notevolmente il tempo impiegato per eseguire tutti i test.
::: moniker-end
::: moniker range=">=vs-2019"
È possibile creare e salvare un elenco di test da eseguire o visualizzare come gruppo. Quando si seleziona una playlist, i test nell'elenco vengono visualizzati in una nuova scheda Esplora test. È possibile aggiungere un test a più playlist.

**Per creare una playlist**, scegliere uno o più test in Esplora Test. Scegliere Aggiungi a playlist nuova playlist dal menu  >  **di scelta rapida.**

![Creare una playlist](../test/media/vs-2019/test-explorer-playlist-16-2.png)

La playlist si apre in una nuova scheda Esplora test. È possibile usare questa playlist una sola volta  e quindi eliminarla oppure fare clic sul pulsante Salva sulla barra degli strumenti della finestra della playlist e quindi selezionare un nome e un percorso per salvare la playlist.

![La playlist si apre in una nuova scheda di Esplora test](../test/media/vs-2019/test-explorer-playlist-tab-16-7.png)

**Per creare una playlist**, scegliere uno o più test in Esplora Test. Fare clic con il pulsante destro del mouse e **scegliere Aggiungi a playlist** Nuova  >  **playlist**.

**Per aprire una playlist**, scegliere l'icona della playlist sulla barra degli strumenti di Visual Studio, quindi scegliere un file di playlist salvato in precedenza dal menu.

**Per modificare una playlist,** è possibile fare clic con il pulsante destro del mouse su qualsiasi test e usare le opzioni di menu per aggiungerla o rimuoverla da una playlist.

A partire Visual Studio 2019 versione 16.7, è possibile scegliere il **pulsante** Modifica sulla barra degli strumenti. Accanto ai test verranno visualizzate le caselle di controllo che mostrano i test inclusi ed esclusi nella playlist. Modificare i gruppi in base alle esigenze.

![Pulsante Modifica playlist](../test/media/vs-2019/test-explorer-playlist-edit-16-7.png)

È anche possibile selezionare o deselezionare le caselle dei gruppi padre nella gerarchia. Questa azione crea una playlist dinamica che aggiorna sempre la playlist in base ai test presenti in tale gruppo. Ad esempio, se si posiziona un segno di spunta accanto a una classe, qualsiasi test aggiunto da tale classe diventa parte di questa playlist. Se si elimina un test da tale classe, questo viene rimosso dalla playlist. Per altre informazioni sulle regole, salvare la playlist con il pulsante Salva sulla barra degli strumenti e aprire il file con estensione *playlist* creato sul disco. Questo file elenca tutte le regole e i singoli test che costituiscono una playlist.

![File XML della playlist](../test/media/vs-2019/test-explorer-playlist-xml-file.png)

Se si vuole creare una playlist per i tratti, usare il formato seguente per MSTest.
```xml
<Playlist Version="2.0">
    <Rule Name="Includes" Match="Any">
        <Property Name="Trait" Value="SchemaUpdateBasic" />
    </Rule>
</Playlist>
```

Usare il formato seguente per xUnit. Assicurarsi che sia presente uno spazio tra il `TestCategory` nome e `[Value]` .
```xml
<Playlist Version="2.0">
  <Rule Name="Includes" Match="Any">
    <Rule Match="All">
      <Property Name="Solution" />
        <Rule Match="Any">
            <Property Name="Trait" Value="TestCategory [Value]" />
        </Rule>
    </Rule>
  </Rule>
</Playlist>
```

::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Colonne di Esplora test

I [gruppi](#test-explorer-groups) sono disponibili anche come colonne in Esplora test, insieme a Tratti, Analisi dello stack, Messaggio di errore e Nome completo. La maggior parte delle colonne non è visibile per impostazione predefinita ed è possibile personalizzare quali colonne visualizzare e l'ordine in cui sono disposte.

![Screenshot dell'Visual Studio Esplora test che mostra un menu con colonne selezionate e un sottomenu con durata, tratti e messaggio di errore selezionati.](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrare, ordinare e ridisporre le colonne di test

Le colonne possono essere filtrate, ordinate e ridisposte.
* Per filtrare in base a tratti specifici, fare clic sull'icona del filtro nella parte superiore della colonna Tratti.

  ![Filtro delle colonne](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Per cambiare l'ordine delle colonne, fare clic su un'intestazione di colonna e trascinarla a sinistra o a destra.

* Per ordinare una colonna, fare clic su un'intestazione di colonna. Non tutte le colonne possono essere ordinate. È anche possibile ordinare in base a una colonna secondaria tenendo premuto il tasto **MAIUSC** e facendo clic su un'intestazione di colonna aggiuntiva.

  ![Ordinamento delle colonne](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Eseguire ricerche e applicare filtri nell'elenco dei test

È anche possibile usare i filtri di ricerca di Esplora Test per limitare i metodi di test nei progetti che vengono visualizzati ed eseguiti.

Quando si digita una stringa nella casella di ricerca **Esplora test** e si preme **INVIO**, l'elenco dei test viene filtrato per visualizzare solo i test i cui nomi completi contengono la stringa.

Per filtrare in base a un criterio diverso:

1. Aprire l'elenco a discesa a destra della casella di ricerca.

2. Scegliere un nuovo criterio.

3. Immettere il valore di filtro tra virgolette. Se si vuole cercare una corrispondenza esatta per la stringa anziché una corrispondenza di contenimento, usare il segno di uguale (=) invece dei due punti (:).

::: moniker range="vs-2017"
![Filtrare i test in Esplora test](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtrare i test in Esplora test](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Le ricerche non fanno distinzione tra maiuscole e minuscole e consentono di trovare la corrispondenza tra la stringa specificata e qualsiasi parte del valore del criterio.

::: moniker range="vs-2017"
|Qualifier|Descrizione|
|-|-----------------|
|**Caratteristica**|Cerca le corrispondenze sia nel valore sia nella categoria dei tratti. La sintassi per specificare i valori e le categorie dei tratti è definita dal framework di unit test.|
|**Progetto**|Cerca le corrispondenze nei nomi dei progetti di test.|
|**Messaggio di errore**|Cerca le corrispondenze nei messaggi di errore definiti dall'utente restituiti da asserzioni non riuscite.|
|**Percorso file**|Cerca le corrispondenze nel nome file completo dei file di origine test.|
|**Nome completo**|Cerca le corrispondenze nel nome completo di spazi dei nomi, classi e metodi di test.|
|**Output**|Cerca nei messaggi di errore definiti dall'utente che vengono scritti in stdout (standard output) o stderr (stderr). La sintassi per specificare i messaggi di output è definita dal framework di unit test.|
|**Risultato**|Cerca le corrispondenze nei nomi delle categorie di Esplora test: **Test non superati**, **Test ignorati**, **Test superati**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Qualifier|Descrizione|
|-|-----------------|
|**State**|Cerca le corrispondenze nei nomi delle categorie di Esplora test: **Test non superati**, **Test ignorati**, **Test superati**.|
|**Tratti**|Cerca le corrispondenze sia nel valore sia nella categoria dei tratti. La sintassi per specificare i valori e le categorie dei tratti è definita dal framework di unit test.|
|**Nome completo**|Cerca le corrispondenze nel nome completo di spazi dei nomi, classi e metodi di test.|
|**Progetto**|Cerca le corrispondenze nei nomi dei progetti di test.|
|**Framework di destinazione**|Cerca le corrispondenze nei nomi delle categorie di Esplora test: **Test non superati**, **Test ignorati**, **Test superati**.|
|**Namespace**|Cerca le corrispondenze negli spazi dei nomi di test.|
|**Classe**|Cerca le corrispondenze nei nomi delle classi di test.|
::: moniker-end

Per escludere un subset dei risultati di un filtro, usare la sintassi seguente:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Ad esempio, `FullName:"MyClass" - FullName:"PerfTest"` restituisce tutti i test che includono "MyClass" nel nome, ad eccezione dei test che includono anche "PerfTest" nel nome.

### <a name="analyze-unit-test-code-coverage"></a>Analizzare il code coverage di unit test

È possibile determinare la quantità di codice del prodotto sottoposta effettivamente a test dagli unit test usando lo strumento per il code coverage di Visual Studio disponibile nell'edizione Visual Studio Enterprise. È possibile eseguire il code coverage su test selezionati oppure su tutti i test in una soluzione.

Per eseguire il code coverage per i metodi di test in una soluzione:

::: moniker range="vs-2017"

1. Scegliere **Test** dalla barra dei menu in alto e quindi scegliere **Analizza code coverage**.

2. Scegliere uno dei comandi seguenti dal sottomenu:

    - **Test selezionati** esegue i metodi di test selezionati in Esplora test.

    - **Tutti i test** esegue tutti i metodi di test nella soluzione.

::: moniker-end

::: moniker range=">=vs-2019"

* Fare clic con il pulsante destro del mouse in Esplora test e **scegliere Analizza code coverage per test selezionati**

::: moniker-end

La finestra **Risultati code coverage** visualizza la percentuale di blocchi di codice del prodotto esaminati in base a riga, funzione, classe, spazio dei nomi e modulo.

Per altre informazioni, vedere [Usare la funzionalità code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Tasti di scelta rapida per i test

I **test** possono essere eseguiti da Esplora test facendo clic con il pulsante destro del mouse nell'editor di codice in un test e scegliendo Esegui test o usando i tasti di scelta rapida predefiniti di Esplora test [in](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) Visual Studio. Alcune combinazioni di tasti sono basate sul contesto. Ciò significa che eseguono o eseguono [il debug dei test](../test/debug-unit-tests-with-test-explorer.md) in base alla posizione in cui si trova il cursore nell'editor di codice. Se il cursore si trova all'interno di un metodo di test, il metodo di test viene eseguito. Se il cursore si trova a livello di classe, vengono eseguiti tutti i test presenti nella classe. Lo stesso si verifica per il livello dello spazio dei nomi.

|Comandi frequenti| Tasti di scelta rapida|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**CTRL** + **R**, **CTRL** + **T**|
|TestExplorer.RunAllTestsInContext|**CTRL** + **R**, **T**|
|TestExplorer.RunAllTests|**CTRL** + **R**, **A**|
|TestExplorer.RepeatLastRun|**CTRL** + **R**, **L**|

> [!NOTE]
> Non è possibile eseguire un test in una classe astratta, poiché i test vengono solo definiti nelle classi astratte ma non ne viene creata l'istanza. Per eseguire i test nelle classi astratte, creare una classe che deriva dalla classe astratta.

::: moniker range=">=vs-2019"
## <a name="test-audio-cue"></a>Testare il segnale audio
Esplora test può riprodurre un suono al termine dell'esecuzione di un test. Sono presenti due suoni: un suono per indicare che l'esecuzione del test è riuscita con tutti i test superati e un secondo suono per indicare che l'esecuzione del test è stata completata con almeno un test non superato. È possibile configurare questi suoni nella finestra di dialogo predefinita Windows 10 audio. Questa funzionalità è disponibile a partire Visual Studio 2019 Update 16.9 Preview 3.

1. Aprire la finestra di dialogo Windows 10 audio predefinita.
2. Passare alla **scheda Suoni.**
3. Trovare la **Microsoft Visual Studio** categorie. Scegliere **i suoni Esecuzione test completata** o Esecuzione **test** non riuscita per selezionare i suoni preimpostati o selezionare il file audio.  
![Windows 10 di dialogo audio](../test/media/default-windows-10-sound-dialog.png)

::: moniker-end
## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire il debug di unit test con Esplora test](../test/debug-unit-tests-with-test-explorer.md)
- [Eseguire uno unit test come processo a 64 bit](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Domande frequenti su Esplora test](test-explorer-faq.md)
