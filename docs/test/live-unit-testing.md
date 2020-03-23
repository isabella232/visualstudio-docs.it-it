---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 1e1a0ec1fd6f2fbdf4f016b1d22db5a6929b5e24
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75851437"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Come configurare e utilizzare Live Unit Testing

Durante lo sviluppo di un'applicazione, Live Unit Test esegue automaticamente tutti gli unit test interessati in background e presenta i risultati e il code coverage in tempo reale. Durante la modifica del codice, Live Unit Testing fornisce commenti e suggerimenti sull'impatto delle modifiche sui test esistenti e indica se il nuovo codice aggiunto è coperto da uno o più test esistenti. Questo ricorda delicatamente di scrivere unit test mentre si stanno facendo correzioni di bug o l'aggiunta di nuove funzionalità.

> [!NOTE]
> Live Unit Testing è disponibile per i progetti in C e Visual Basic destinati a .NET Core o .NET Framework nell'edizione Enterprise di Visual Studio.

Quando si utilizza Live Unit Testing per i test, vengono mantenuti i dati sullo stato dei test. L'utilizzo di dati persistenti consente ai Live Unit Test di offrire prestazioni superiori durante l'esecuzione dei test in modo dinamico in risposta alle modifiche del codice.

## <a name="supported-test-frameworks"></a>Framework di test supportati

Live Unit Testing è compatibile con i tre framework di unit test elencati nella tabella seguente. Viene inoltre visualizzata la versione minima supportata degli adattatori e dei framework. I framework di unit test sono tutti disponibili su NuGet.org.

|Framework di test  |Versione minima dell'adattatore di Visual Studio  |Versione minima del framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versione 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versione 3.5.1 |NUnit versione 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se si dispone di progetti di test basati su MSTest meno recenti che fanno riferimento a Microsoft.VisualStudio.QualityTools.UnitTestFramework e non si desidera passare ai pacchetti NuGet MSTest più recenti, eseguire l'aggiornamento a Visual Studio 2019 o Visual Studio 2017.

In alcuni casi, potrebbe essere necessario ripristinare in modo esplicito i pacchetti NuGet a cui fa riferimento un progetto affinché il funzionamento di Live Unit Testing. A tale scopo, è possibile eseguire una compilazione esplicita della soluzione (selezionare **Compila** > **soluzione** di compilazione dal menu di Visual Studio di primo livello) o ripristinando i pacchetti nella soluzione (fare clic con il pulsante destro del mouse sulla soluzione e selezionare Ripristina **pacchetti NuGet**).

## <a name="configure"></a>Configurare

Configurare Live Unit Testing selezionando**Opzioni** **degli strumenti** > dalla barra dei menu di Visual Studio di primo livello e quindi selezionando **Live Unit Testing** nel riquadro sinistro della finestra di dialogo **Opzioni.**

> [!TIP]
> Dopo aver abilitato Live Unit Testing (vedere la sezione successiva, [Avviare, sospendere e interrompere Live Unit Testing),](#start-pause-and-stop)è anche possibile aprire la finestra di dialogo **Opzioni** selezionando **Test** > delle > **opzioni**di unit**test dinamiche**.

L'immagine seguente mostra le opzioni di configurazione di Live Unit Testing disponibili nella finestra di dialogo:

![Opzioni di configurazione di Live Unit Testing](./media/lut-options.png)

Le opzioni configurabili includono:

- Sospensione dell'esecuzione di Live Unit Testing in caso di compilazione e debug di una soluzione.

- Sospensione dell'esecuzione di Live Unit Testing quando l'alimentazione a batteria del sistema scende sotto una soglia specificata.

- Esecuzione automatica di Live Unit Testing all'apertura di una soluzione.

- Abilitazione del simbolo di debug e generazione di commenti in formato documentazione XML.

- Directory in cui archiviare i dati salvati in modo permanente.

- Possibilità di eliminare tutti i dati persistenti. Ciò è utile quando Live Unit Testing si comporta in modo imprevedibile o imprevisto, il che suggerisce che i dati persistenti sono danneggiati.

- Intervallo dopo il quale si verifica il timeout di un test case. Il valore predefinito è 30 secondi.

- Numero massimo di processi di test creati da Live Unit Testing.

- Quantità massima di memoria che i processi di Live Unit Testing possono utilizzare.

- Livello delle informazioni scritte nella finestra **Output** di Live Unit Testing.

   È possibile scegliere di non visualizzare informazioni di log (**Nessuno**), solo i messaggi errore (**Errore**), messaggi di errore e messaggi informativi (**Informazioni**, che corrisponde al valore predefinito) o tutti i dettagli (**Dettagliato**).

   Per visualizzare l'output dettagliato nella finestra **Output** di Live Unit Testing, è anche possibile assegnare il valore "1" a una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e riavviare Visual Studio.

   Per acquisire in un file i messaggi di log dettagliati di MSBuild restituiti da Live Unit Testing, impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildLog` sul nome del file in cui salvare il log.

## <a name="start-pause-and-stop"></a>Avviare, mettere in pausa e arrestare

Per abilitare Live Unit Testing, selezionare **Test** > **Live Unit Testing** > **Start** dal menu di Visual Studio di primo livello. Quando Live Unit Testing è abilitato, le opzioni disponibili nel menu **Live Unit Testing** cambiano da un singolo elemento, **Start**, a **Pausa** e **Interrompi**:

- **Pausa** sospende temporaneamente Live Unit Testing.

  Quando Live Unit Testing viene sospeso, la visualizzazione della copertura non viene visualizzata nell'editor, ma tutti i dati raccolti vengono mantenuti. Per riprendere l'esecuzione di Live Unit Testing, selezionare **Continua** dal menu di Live Unit Testing. Live Unit Testing esegue il lavoro necessario per recuperare il ritardo con tutte le modifiche apportate mentre è stato messo in pausa e aggiorna i glifi in modo appropriato.

- **Stop** interrompe completamente Live Unit Testing. Con questa opzione tutti i dati raccolti vengono rimossi.

> [!NOTE]
> Se si avvia Live Unit Testing in una soluzione che non include un progetto di unit test, le opzioni **Pausa** e **Interrompi** vengono visualizzate nel menu **Live Unit Testing,** ma non viene avviato. Nella finestra **Output** viene visualizzato il messaggio "Nessun adattatore di test supportato fa riferimento a questa soluzione...".

È possibile sospendere temporaneamente o arrestare completamente Live Unit Testing in qualsiasi momento. È possibile eseguire questa operazione, ad esempio, se ci si è nel bel mezzo di un refactoring e si sa che i test verranno interrotti per un certo periodo di tempo.

## <a name="view-coverage-visualization"></a>Visualizzare la visualizzazione della copertura

Dopo l'abilitazione, Live Unit Testing aggiorna ogni riga di codice nell'editor di Visual Studio per mostrare se il codice che si sta scrivendo è coperto da unit test e se i test che lo coprono vengono superati. L'immagine seguente mostra righe di codice con test superati e non superati, nonché righe di codice non coperte dai test. Le righe contraddistinte da un segno di spunta "✓" verde sono coperte solo da test superati, quelle contraddistinte da una "x" rossa sono coperte da uno o più test non superati, mentre quelle contraddistinte da un simbolo "➖" blu non sono coperte da alcun test.

![Code coverage in Visual Studio](./media/lut-codewindow.png)

La visualizzazione di copertura di Live Unit Testing viene aggiornata immediatamente quando si modifica il codice nell'editor di codice. Durante l'elaborazione delle modifiche, la visualizzazione cambia per indicare che i dati non sono aggiornati aggiungendo un'immagine del timer rotondo sotto i simboli di passaggio, di esito negativo e non coperto, come illustrato nell'immagine seguente.

![Code coverage in Visual Studio con l'icona del timerCode coverage in Visual Studio with timer icon](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Ottenere informazioni sullo stato del testGet information about test status

Per visualizzare il numero di test eseguiti su una certa riga, è possibile passare il puntatore sul simbolo di test superato o non superato nella finestra del codice. Per visualizzare lo stato dei singoli test, selezionare il simbolo:

![Test status for a symbol in Visual Studio](./media/lut-failedinfo.png)

Oltre a fornire i nomi e il risultato dei test, la descrizione comando consente di rieseguire o eseguire il debug del set di test. Se si selezionano uno o più test nella descrizione comando, è anche possibile eseguire o sottoporre a debug solo tali test. Ciò consente di eseguire il debug dei test senza uscire dalla finestra del codice. Durante il debug, oltre a osservare eventuali punti di interruzione già configurati, l'esecuzione del programma viene sospesa quando il debugger esegue un metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> che restituisce un risultato imprevisto.

Quando si passa il puntatore su un test non superato nella descrizione comando, questa si espande e visualizza informazioni aggiuntive sull'errore, come illustrato nell'immagine seguente. Per passare direttamente a un test non riuscito, fare doppio clic su di esso nella descrizione comando.

![Informazioni sulla descrizione comando di test non riuscita in Visual StudioFailed test tooltip info in Visual Studio](./media/lut-failedmsg.png)

Quando si passa al test non riuscito, Live Unit Testing indica visivamente nella firma del metodo i test con:

- passato (indicato da un becher mezzo pieno insieme a un verde "-")
- fallito (un becher mezzo pieno🞩insieme a un rosso " ")
- non sono coinvolti in Live Unit Testing (un becher mezzo pieno insieme a un "➖") blu

I metodi non di test non sono decorati con simboli. Nell'immagine seguente vengono illustrati tutti e quattro i tipi di metodi.

![Metodi di test in Visual Studio con simbolo pass o fail](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnosticare e correggere gli errori di test

Dal test non superato, è possibile eseguire facilmente il debug del codice del prodotto, apportare modifiche e continuare a sviluppare l'applicazione. Poiché Live Unit Testing viene eseguito in background, non è necessario arrestare e riavviare Live Unit Testing durante il ciclo di debug, modifica e continuazione.

Ad esempio, l'errore di test mostrato nell'immagine precedente è stato causato da `true` un presupposto <xref:System.Char.IsLower%2A?displayProperty=fullName> non corretto nel metodo di test restituito da caratteri non alfabetici quando vengono passati al metodo. Dopo aver corretto il metodo di test, tutti i test devono essere superati. Non è necessario sospendere o interrompere Live Unit Testing.

## <a name="test-explorer"></a>Esplora test

**Esplora test** fornisce un'interfaccia che consente di eseguire ed eseguire il debug dei test e analizzare i risultati dei test. Live Unit Testing si integra con **Esplora test**. Quando Live Unit Testing non è abilitato o è stato arrestato, **Esplora Test** visualizza lo stato degli unit test durante l'ultima esecuzione di un test. Se si apportano modifiche al codice sorgente, è necessario eseguire di nuovo i test. Quando invece è abilitato Live Unit Testing, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è necessario eseguire in modo esplicito gli unit test.

> [!TIP]
> Aprire **Esplora test** selezionando **Test** > **di Esplora test** di**Windows** > dal menu di Visual Studio di primo livello.

È possibile notare nella finestra **Esplora test** che alcuni test sono sbiaditi. Ad esempio, quando si attiva Live Unit Testing dopo l'apertura di un progetto salvato in precedenza, la finestra **Esplora test** era sbiadita tutto tranne il test non superato, come illustrato nell'immagine seguente. In questo caso, Live Unit Testing ha rieseguito il test non riuscito, ma non ha rieseguito i test riusciti. Ciò è dovuto al fatto che i dati persistenti di Live Unit Test indicano che non sono state apportate modifiche dall'ultima esecuzione dei test.

![Test non superato in Esplora testFailed test in Test Explorer](media/lut-test-explorer.png)

È possibile eseguire nuovamente tutti i test visualizzati dissolvenza selezionando le opzioni **Esegui tutto** o **Esegui** dal menu **Esplora test.** In alternativa, selezionare uno o più test dal menu **Esplora test,** fare clic con il pulsante destro del mouse e scegliere **Esegui test selezionati** o Esegui debug test **selezionati** dal menu di scelta rapida. Quando i test vengono eseguiti, vengono visualizzati nella parte superiore.

Esistono alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Ecco alcune di queste differenze:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati.
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Nella finestra **Esplora test** è possibile scegliere di eseguire più test in parallelo.

## <a name="large-solutions"></a>Soluzioni di grandi dimensioni

Se la soluzione include 10 o più progetti, Visual Studio visualizza la finestra di dialogo seguente quando si esegue la funzionalità:If your solution has 10 or more projects, Visual Studio displays the following dialog when you:

- avviare Live Unit Testing e non sono presenti dati persistenti
- selezionare **Strumenti** > **Opzioni Live** > **Unit Testing** > **Eliminare dati persistenti**

![Finestra di dialogo di Live Unit Testing per progetti di grandi dimensioni](media/lut-large-project.png)

La finestra di dialogo avvisa che l'esecuzione dinamica di un numero elevato di test in progetti di grandi dimensioni può influire notevolmente sulle prestazioni. Se si seleziona **OK**, Live Unit Testing esegue tutti i test della soluzione. Se si seleziona **Annulla**, è possibile selezionare i test da eseguire. Nella sezione seguente viene illustrato come eseguire questa operazione.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Includere ed escludere progetti e metodi di test

Per le soluzioni con molti progetti di test, è possibile controllare quali progetti e singoli metodi in un progetto partecipano a Live Unit Testing. Se ad esempio una soluzione contiene centinaia di progetti di test, è possibile selezionare un set specifico di progetti di test da includere in Live Unit Testing. Per eseguire questa operazione, è possibile escludere tutti i test nel progetto o nella soluzione, includere o escludere la maggior parte dei test o escludere singoli test. In Live Unit Testing lo stato di inclusione/esclusione viene salvato come impostazione utente e memorizzato alla chiusura o alla riapertura di una soluzione.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Escludere tutti i test in un progetto o in una soluzioneExclude all tests in a project or solution

Per selezionare i singoli progetti negli unit test, eseguire le operazioni seguenti dopo aver avviato Live Unit Testing:

1. Fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Test attivi** > **Escludi** per escludere l'intera soluzione.
1. Fare clic con il pulsante destro del mouse su ogni progetto di test che si desidera includere nei test e scegliere**Includi** **test** > in tempo reale .

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Escludere singoli test dalla finestra dell'editor di codiceExclude individual tests from the code editor window

Per includere o escludere singoli metodi di test, è possibile usare la finestra dell'editor del codice. Fare clic con il pulsante destro del mouse sulla firma del metodo di test nella finestra dell'editor di codice, quindi selezionare una delle opzioni seguenti:

- **Test in** > tempo reale**Includere \<i>di metodo selezionati**
- **Test in** > tempo reale**Escludi \<>metodo selezionato**
- **I test** > in tempo reale**escludono tutto tranne \<** il metodo selezionato>

### <a name="exclude-tests-programmatically"></a>Escludere i test a livello di codiceExclude tests programmatically

È possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> per evitare a livello di codice che metodi, classi o strutture restituiscano informazioni sul code coverage in Live Unit Testing.

Utilizzare i seguenti attributi per escludere singoli metodi da Live Unit Testing:

- Per xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Utilizzare i seguenti attributi per escludere un intero assembly di test da Live Unit Testing:

- Per xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vedere anche

- [Strumenti di test del codice](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog di Live Unit Testing](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Domande frequenti sugli unit test in tempo reale](live-unit-testing-faq.md)
- [Video di Channel 9: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
