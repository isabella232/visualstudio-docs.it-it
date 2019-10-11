---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: gewarren
ms.author: gewarren
ms.workload:
- dotnet
ms.openlocfilehash: 646a8680211d7d79ea24a1b5b62d78eb6955b5f7
ms.sourcegitcommit: 1a3c2ca995fd44fc72741b3a100c6e57f4f8702c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262330"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Come configurare e usare Live Unit Testing

Durante lo sviluppo di un'applicazione, Live Unit Testing esegue automaticamente tutti gli unit test interessati in background e Visualizza i risultati e i code coverage in tempo reale. Durante la modifica del codice, Live Unit Testing fornisce commenti e suggerimenti sull'impatto delle modifiche sui test esistenti e indica se il nuovo codice aggiunto è coperto da uno o più test esistenti. In questo modo si ricorda di scrivere unit test durante la creazione di correzioni di bug o l'aggiunta di nuove funzionalità.

> [!NOTE]
> Live Unit Testing è disponibile per C# i progetti di e Visual Basic destinati a .NET Core o .NET Framework nell'edizione Enterprise di Visual Studio.

Quando si usa Live Unit Testing per i test, vengono mantenuti i dati sullo stato dei test. L'uso di dati salvati in modo permanente consente Live Unit Testing offrire prestazioni migliori durante l'esecuzione dinamica dei test in risposta alle modifiche del codice.

## <a name="supported-test-frameworks"></a>Framework di test supportati

Live Unit Testing è compatibile con i tre framework di unit test elencati nella tabella seguente. Viene visualizzata anche la versione minima supportata degli adapter e dei Framework. I framework di unit test sono tutti disponibili su NuGet.org.

|Framework di test  |Versione minima dell'adattatore di Visual Studio  |Versione minima del framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versione 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versione 3.5.1 |NUnit versione 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se sono presenti progetti di test basati su MSTest precedenti che fanno riferimento a Microsoft. VisualStudio. QualityTools. UnitTestFramework e non si vuole passare ai pacchetti NuGet di MSTest più recenti, eseguire l'aggiornamento a Visual Studio 2019 o Visual Studio 2017.

In alcuni casi, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui fa riferimento un progetto per consentire il funzionamento del Live Unit Testing. È possibile eseguire questa operazione eseguendo una compilazione esplicita della soluzione (selezionare **compila** > **Ricompila soluzione** dal menu di primo livello di Visual Studio) o ripristinando i pacchetti nella soluzione (fare clic con il pulsante destro del mouse sulla soluzione e selezionare **Ripristina NuGet Pacchetti**).

## <a name="configure"></a>Configurazione

Configurare Live Unit Testing selezionando **strumenti** >  dalla barra dei menu di primo**livello di Visual** studio, quindi selezionando **Live unit testing** nel riquadro sinistro della finestra di dialogo **Opzioni** .

> [!TIP]
> Dopo l'abilitazione di Live Unit Testing (vedere la sezione successiva, [avviare, sospendere e arrestare Live unit testing](#start-pause-and-stop)), è anche possibile aprire la finestra di dialogo **Opzioni** selezionando **test** > **Live unit testing** **Opzioni** > .

Nella figura seguente sono illustrate le opzioni di configurazione Live Unit Testing disponibili nella finestra di dialogo:

![Opzioni di configurazione Live Unit Testing](./media/lut-options.png)

Le opzioni configurabili includono:

- Sospensione dell'esecuzione di Live Unit Testing in caso di compilazione e debug di una soluzione.

- Sospensione dell'esecuzione di Live Unit Testing quando l'alimentazione a batteria del sistema scende sotto una soglia specificata.

- Esecuzione automatica di Live Unit Testing all'apertura di una soluzione.

- Abilitazione del simbolo di debug e generazione di commenti in formato documentazione XML.

- Directory in cui archiviare i dati salvati in modo permanente.

- Possibilità di eliminare tutti i dati persistenti. Si tratta di un'operazione utile quando Live Unit Testing si comporta in modo imprevedibile o imprevisto, il che suggerisce che i dati salvati in modo permanente risultano danneggiati.

- Intervallo dopo il quale si verifica il timeout di un test case. Il valore predefinito è 30 secondi.

- Numero massimo di processi di test creati da Live Unit Testing.

- Quantità massima di memoria che i processi di Live Unit Testing possono utilizzare.

- Livello delle informazioni scritte nella finestra **Output** di Live Unit Testing.

   È possibile scegliere di non visualizzare informazioni di log (**Nessuno**), solo i messaggi errore (**Errore**), messaggi di errore e messaggi informativi (**Informazioni**, che corrisponde al valore predefinito) o tutti i dettagli (**Dettagliato**).

   Per visualizzare l'output dettagliato nella finestra **Output** di Live Unit Testing, è anche possibile assegnare il valore "1" a una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e riavviare Visual Studio.

   Per acquisire in un file i messaggi di log dettagliati di MSBuild restituiti da Live Unit Testing, impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildLog` sul nome del file in cui salvare il log.

## <a name="start-pause-and-stop"></a>Avvio, sospensione e arresto

Per abilitare Live Unit Testing, selezionare **Test** > **Live unit testing** > **Avvia** dal menu di primo livello di Visual Studio. Quando Live Unit Testing è abilitato, le opzioni disponibili nel menu **Live unit testing** cambiano da un singolo elemento, **Start**, per **sospendere**, **arrestare**e **reimpostare clean**:

- **Sospendi sospende temporaneamente Live unit testing** .

  Quando Live Unit Testing viene sospesa, la visualizzazione del code coverage non viene visualizzata nell'editor, ma tutti i dati raccolti vengono conservati. Per riprendere l'esecuzione di Live Unit Testing, selezionare **Continua** dal menu di Live Unit Testing. Live Unit Testing esegue il lavoro necessario per aggiornare tutte le modifiche apportate durante la sospensione e aggiornare i glifi in modo appropriato.

- **Arresta completamente Live unit testing** . Con questa opzione tutti i dati raccolti vengono rimossi.

- **Reimposta** Live unit testing Elimina i dati salvati in modo permanente, quindi riavvia Live unit testing.

> [!NOTE]
> Se si avvia Live Unit Testing in una soluzione che non include un progetto di unit test, le opzioni **Pausa**, **Interrompi**, e **Reset Clean** (Reimposta e pulisci) vengono visualizzate nel menu **Live Unit Testing**, ma Live Unit Testing non viene avviato. Nella finestra **output** viene visualizzato un messaggio che inizia con "nessun adattatore di test supportato a cui fa riferimento questa soluzione...".

È possibile sospendere temporaneamente o arrestare completamente Live Unit Testing in qualsiasi momento. Questa operazione può essere eseguita, ad esempio, se si sta eseguendo il refactoring e si è certi che i test verranno interrotti per un periodo di tempo.

## <a name="view-coverage-visualization"></a>Visualizzazione di code coverage

Dopo l'abilitazione, Live Unit Testing aggiorna ogni riga di codice nell'editor di Visual Studio in modo da indicare se il codice scritto è coperto da unit test e se i test che lo coprono passano. Nell'immagine seguente vengono illustrate le righe di codice con test superati e non superati, oltre a righe di codice non coperte da test. Le righe contraddistinte da un segno di spunta "✓" verde sono coperte solo da test superati, quelle contraddistinte da una "x" rossa sono coperte da uno o più test non superati, mentre quelle contraddistinte da un simbolo "➖" blu non sono coperte da alcun test.

![Code coverage in Visual Studio](./media/lut-codewindow.png)

La visualizzazione del code coverage Live Unit Testing viene aggiornata immediatamente quando si modifica il codice nell'editor di codice. Durante l'elaborazione delle modifiche, la visualizzazione cambia per indicare che i dati non sono aggiornati aggiungendo un'immagine round timer al di sotto dei simboli passati, non riusciti e non analizzati, come illustrato nella figura seguente.

![Code coverage in Visual Studio con icona timer](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Ottenere informazioni sullo stato dei test

Per visualizzare il numero di test eseguiti su una certa riga, è possibile passare il puntatore sul simbolo di test superato o non superato nella finestra del codice. Per visualizzare lo stato dei singoli test, selezionare il simbolo:

![Stato del test per un simbolo in Visual Studio](./media/lut-failedinfo.png)

Oltre a fornire i nomi e il risultato dei test, la descrizione comando consente di eseguire di nuovo o eseguire il debug del set di test. Se si selezionano uno o più test nella descrizione comando, è anche possibile eseguire o sottoporre a debug solo tali test. Ciò consente di eseguire il debug dei test senza uscire dalla finestra del codice. Quando si esegue il debug, oltre a osservare eventuali punti di interruzione già impostati, l'esecuzione del programma viene sospesa quando il debugger esegue un metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> che restituisce un risultato imprevisto.

Quando si passa il puntatore su un test non superato nella descrizione comando, questa si espande e visualizza informazioni aggiuntive sull'errore, come illustrato nell'immagine seguente. Per passare direttamente a un test non superato, fare doppio clic su di esso nella descrizione comando.

![Informazioni sulla descrizione comando test non riuscite in Visual Studio](./media/lut-failedmsg.png)

Quando si passa al test non superato, Live Unit Testing indica visivamente nella firma del metodo i test che hanno:

- superato (indicato da un becher a metà pieno insieme a una "✓" verde)
- failed (un becher a metà pieno insieme a un "🞩")
- non sono interessati all'Live Unit Testing (un becher a metà pieno insieme a un "➖" blu)

I metodi non di test non sono decorati con simboli. Nell'immagine seguente vengono illustrati tutti e quattro i tipi di metodi.

![Metodi di test in Visual Studio con simbolo Pass o Fail](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnosticare e correggere gli errori di test

Dal test non superato, è possibile eseguire facilmente il debug del codice del prodotto, apportare modifiche e continuare a sviluppare l'applicazione. Poiché Live Unit Testing viene eseguito in background, non è necessario arrestare e riavviare Live Unit Testing durante il ciclo di debug, modifica e continuazione.

L'errore di test illustrato nell'immagine precedente, ad esempio, è stato causato da un presupposto non corretto nel metodo di test in base al quale i caratteri non alfabetici restituiscono `true` quando vengono passati al metodo <xref:System.Char.IsLower%2A?displayProperty=fullName>. Dopo aver corretto il metodo di test, tutti i test devono essere superati. Non è necessario sospendere o arrestare Live Unit Testing.

## <a name="test-explorer"></a>Esplora test

**Esplora test** fornisce un'interfaccia che consente di eseguire ed eseguire il debug dei test e analizzare i risultati dei test. Live Unit Testing si integra con **Esplora test**. Quando Live Unit Testing non è abilitato o è stato arrestato, **Esplora Test** visualizza lo stato degli unit test durante l'ultima esecuzione di un test. Se si apportano modifiche al codice sorgente, è necessario eseguire di nuovo i test. Quando invece è abilitato Live Unit Testing, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è necessario eseguire gli unit test in modo esplicito.

> [!TIP]
> Aprire **Esplora test** selezionando **test** > **Windows** > **Esplora test** dal menu di primo livello di Visual Studio.

Come si può notare, nella finestra **Esplora test** alcuni test sono visualizzati in modo attenuato. Ad esempio, quando si Abilita Live Unit Testing dopo l'apertura di un progetto salvato in precedenza, la finestra **Esplora test** ha eliminato tutti i test, tranne quelli non superati, come illustrato nella figura seguente. In questo caso, Live Unit Testing ha rieseguito il test non riuscito, ma non ha eseguito nuovamente i test riusciti. Ciò è dovuto al fatto che Live Unit Testing dati salvati in precedenza indicano che non sono state apportate modifiche dopo l'ultima esecuzione dei test.

![Test non superato in Esplora test](media/lut-test-explorer.png)

È possibile rieseguire tutti i test visualizzati come sbiaditi selezionando le opzioni **Esegui tutto** o **Esegui** dal menu **Esplora test** . In alternativa, selezionare uno o più test nel menu **Esplora test** , fare clic con il pulsante destro del mouse su, quindi scegliere **Esegui test selezionati** o Esegui **debug test selezionati** dal menu di scelta rapida. Quando i test vengono eseguiti, vengono visualizzati nella parte superiore.

Esistono alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Ecco alcune di queste differenze:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati.
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Nella finestra **Esplora test** è possibile scegliere di eseguire più test in parallelo.

## <a name="large-solutions"></a>Soluzioni di grandi dimensioni

Se la soluzione contiene 10 o più progetti, Visual Studio Visualizza la finestra di dialogo seguente quando:

- avvia Live Unit Testing e non sono presenti dati salvati in permanenza
- Selezionare **Test** > **Live unit testing** > **Reimposta Pulisci**

![Finestra di dialogo di Live Unit Testing per progetti di grandi dimensioni](media/lut-large-project.png)

La finestra di dialogo avvisa che l'esecuzione dinamica di un numero elevato di test in progetti di grandi dimensioni può influire gravemente sulle prestazioni. Se si seleziona **OK**, Live Unit Testing esegue tutti i test della soluzione. Se si seleziona **Annulla**, è possibile selezionare i test da eseguire. Nella sezione seguente viene illustrato come eseguire questa operazione.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Includere ed escludere progetti e metodi di test

Per le soluzioni con molti progetti di test, è possibile controllare quali progetti e singoli metodi di un progetto partecipano a Live Unit Testing. Se ad esempio una soluzione contiene centinaia di progetti di test, è possibile selezionare un set specifico di progetti di test da includere in Live Unit Testing. Esistono diversi modi per eseguire questa operazione, a seconda che si desideri escludere tutti i test nel progetto o nella soluzione, includere o escludere la maggior parte dei test oppure escludere i singoli test. In Live Unit Testing lo stato di inclusione/esclusione viene salvato come impostazione utente e memorizzato alla chiusura o alla riapertura di una soluzione.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Escludi tutti i test in un progetto o in una soluzione

Per selezionare i singoli progetti negli unit test, eseguire le operazioni seguenti dopo aver avviato Live Unit Testing:

1. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Test attivi** > **Escludi** per escludere l'intera soluzione.
1. Fare clic con il pulsante destro del mouse su ogni progetto di test da includere nei test e scegliere **Test attivi** > **Includi**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Escludere i singoli test dalla finestra dell'editor di codice

Per includere o escludere singoli metodi di test, è possibile usare la finestra dell'editor del codice. Fare clic con il pulsante destro del mouse sulla firma del metodo di test nella finestra dell'editor di codice e quindi selezionare una delle opzioni seguenti:

- I **test dinamici** > **includono il metodo \<selected >**
- I **test dinamici** > **escludono il metodo \<selected >**
- I **test Live** > **escludono tutti i metodi, tranne \<selected >**

### <a name="exclude-tests-programmatically"></a>Escludi i test a livello di codice

È possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> per evitare a livello di codice che metodi, classi o strutture restituiscano informazioni sul code coverage in Live Unit Testing.

Usare gli attributi seguenti per escludere i singoli metodi dal Live Unit Testing:

- Per xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Usare gli attributi seguenti per escludere un intero assembly di test da Live Unit Testing:

- Per xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vedere anche

- [Strumenti di test del codice](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog di Live Unit Testing](https://go.microsoft.com/fwlink/?linkid=842514)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
- [Video di Channel 9: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
