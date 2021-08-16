---
title: Live Unit Testing
description: Informazioni sulle Live Unit Testing durante lo sviluppo di applicazioni, inclusi i framework supportati e su come configurare Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: e26fe6aceeb08ad4c46411adda2a7c6d628de19e7ae386ff7b1b88b3bf16d70e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441243"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Come configurare e usare Live Unit Testing

Durante lo sviluppo di un'applicazione, Live Unit Testing automaticamente gli unit test influenzati in background e presenta i risultati e code coverage in tempo reale. Durante la modifica del codice, Live Unit Testing fornisce commenti e suggerimenti sull'impatto delle modifiche sui test esistenti e indica se il nuovo codice aggiunto è coperto da uno o più test esistenti. In questo modo si ricorda di scrivere unit test quando si apportano correzioni di bug o si aggiungono nuove funzionalità.

> [!NOTE]
> Live Unit Testing è disponibile per progetti C# e Visual Basic che hanno come destinazione .NET Core o .NET Framework nell'Enterprise di Visual Studio.

Quando si usa Live Unit Testing per i test, vengono mantenuti i dati relativi allo stato dei test. L'uso di dati persistenti Live Unit Testing offrire prestazioni superiori durante l'esecuzione dinamica dei test in risposta alle modifiche del codice.

## <a name="supported-test-frameworks"></a>Framework di test supportati

Live Unit Testing è compatibile con i tre framework di unit test elencati nella tabella seguente. Viene visualizzata anche la versione minima supportata dei relativi adapter e framework. I framework di unit test sono tutti disponibili su NuGet.org.

|Framework di test  |Versione minima dell'adattatore di Visual Studio  |Versione minima del framework  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versione 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versione 3.5.1 |NUnit versione 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se si hanno progetti di test basati su MSTest meno recenti che fanno riferimento a Microsoft.VisualStudio.QualityTools.UnitTestFramework e non si vuole passare ai pacchetti NuGet MSTest più recenti, eseguire l'aggiornamento a Visual Studio 2019 o Visual Studio 2017.

In alcuni casi, potrebbe essere necessario ripristinare in modo esplicito NuGet pacchetti a cui fa riferimento un progetto per Live Unit Testing funzionamento. A tale scopo, è possibile eseguire una compilazione esplicita della soluzione (selezionare Compila ricompila soluzione dal menu Visual Studio di primo livello) o ripristinando i pacchetti nella soluzione (fare clic con il pulsante destro del mouse sulla soluzione e scegliere Ripristina pacchetti  >   **NuGet**).

## <a name="configure"></a>Configurare

Configurare Live Unit Testing selezionando Opzioni strumenti dalla barra dei menu Visual Studio di primo livello e quindi selezionando Live Unit Testing nel riquadro sinistro della finestra di dialogo  >   Opzioni.  

> [!TIP]
> Dopo Live Unit Testing abilitata (vedere la sezione successiva, [Avviare,](#start-pause-and-stop)sospendere e arrestare  Live Unit Testing ), è anche possibile aprire la finestra di dialogo Opzioni selezionando Test  >  **Live Unit Testing**  >  **Opzioni**.

L'immagine seguente mostra le Live Unit Testing di configurazione disponibili nella finestra di dialogo:

![Live Unit Testing di configurazione](./media/lut-options.png)

Le opzioni configurabili includono:

- Sospensione dell'esecuzione di Live Unit Testing in caso di compilazione e debug di una soluzione.

- Sospensione dell'esecuzione di Live Unit Testing quando l'alimentazione a batteria del sistema scende sotto una soglia specificata.

- Esecuzione automatica di Live Unit Testing all'apertura di una soluzione.

- Abilitazione del simbolo di debug e generazione di commenti in formato documentazione XML.

- Directory in cui archiviare i dati salvati in modo permanente.

- Possibilità di eliminare tutti i dati persistenti. Ciò è utile quando Live Unit Testing si comporta in modo imprevedibile o imprevisto, il che suggerisce che i dati persistenti sono danneggiati.

- Intervallo dopo il quale un test case timeout. Il valore predefinito è 30 secondi.

- Numero massimo di processi di test creati da Live Unit Testing.

- Quantità massima di memoria che i processi di Live Unit Testing possono utilizzare.

- Livello delle informazioni scritte nella finestra **Output** di Live Unit Testing.

   È possibile scegliere di non visualizzare informazioni di log (**Nessuno**), solo i messaggi errore (**Errore**), messaggi di errore e messaggi informativi (**Informazioni**, che corrisponde al valore predefinito) o tutti i dettagli (**Dettagliato**).

   Per visualizzare l'output dettagliato nella finestra **Output** di Live Unit Testing, è anche possibile assegnare il valore "1" a una variabile di ambiente a livello di utente denominata `VS_UTE_DIAGNOSTICS` e riavviare Visual Studio.

   Per acquisire in un file i messaggi di log dettagliati di MSBuild restituiti da Live Unit Testing, impostare la variabile di ambiente a livello di utente `LiveUnitTesting_BuildLog` sul nome del file in cui salvare il log.

## <a name="start-pause-and-stop"></a>Avviare, sospendere e arrestare

Per abilitare Live Unit Testing, selezionare **Test** Live Unit Testing Start dal menu Visual Studio  >    >   livello superiore. Quando Live Unit Testing abilitata, le opzioni disponibili nel **menu** Live Unit Testing modificano da una singola voce, **Start**, a **Pause** and **Stop**:

- **Sospendi** sospende Live Unit Testing.

  Quando Live Unit Testing viene sospesa, la visualizzazione di code coverage non viene visualizzata nell'editor, ma tutti i dati raccolti vengono mantenuti. Per riprendere l'esecuzione di Live Unit Testing, selezionare **Continua** dal menu di Live Unit Testing. Live Unit Testing esegue le operazioni necessarie per recuperare tutte le modifiche apportate durante la sospensione e aggiorna i glifi in modo appropriato.

- **Arresta** arresta completamente Live Unit Testing. Con questa opzione tutti i dati raccolti vengono rimossi.

> [!NOTE]
> Se si avvia Live Unit Testing in una soluzione che non include un  progetto  unit test, le opzioni Sospendi e Arresta vengono visualizzate nel menu **Live Unit Testing,** ma Live Unit Testing non viene avviata. Nella **finestra Output** viene visualizzato un messaggio che indica che la soluzione non fa riferimento a nessun adattatore di test supportato.

È possibile sospendere temporaneamente o arrestare completamente Live Unit Testing in qualsiasi momento. È possibile eseguire questa operazione, ad esempio, se si è nel mezzo di un refactoring e si sa che i test verranno interrotti per un po'.

## <a name="view-coverage-visualization"></a>Visualizzare la visualizzazione di code coverage

Dopo che è stato abilitato, Live Unit Testing aggiorna ogni riga di codice nell'editor di Visual Studio per indicare se il codice scritto è coperto da unit test e se i test che lo coprono vengono superati. L'immagine seguente mostra righe di codice con test superati e non superati, nonché righe di codice non coperte dai test. Le righe contraddistinte da un segno di spunta "✓" verde sono coperte solo da test superati, quelle contraddistinte da una "x" rossa sono coperte da uno o più test non superati, mentre quelle contraddistinte da un simbolo "➖" blu non sono coperte da alcun test.

![Code coverage in Visual Studio](./media/lut-codewindow.png)

Live Unit Testing di code coverage viene aggiornata immediatamente quando si modifica il codice nell'editor di codice. Durante l'elaborazione delle modifiche, la visualizzazione cambia per indicare che i dati non sono aggiornati aggiungendo un'immagine del timer di arrotondamento sotto i simboli di passaggio, errore e non coperti, come illustrato nell'immagine seguente.

![Code coverage in Visual Studio con l'icona del timer](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Ottenere informazioni sullo stato dei test

Per visualizzare il numero di test eseguiti su una certa riga, è possibile passare il puntatore sul simbolo di test superato o non superato nella finestra del codice. Per visualizzare lo stato dei singoli test, selezionare il simbolo:

![Stato del test per un simbolo in Visual Studio](./media/lut-failedinfo.png)

Oltre a fornire i nomi e il risultato dei test, la descrizione comando consente di rieseguire o eseguire il debug del set di test. Se si selezionano uno o più test nella descrizione comando, è anche possibile eseguire o sottoporre a debug solo tali test. Ciò consente di eseguire il debug dei test senza uscire dalla finestra del codice. Durante il debug, oltre a osservare eventuali punti di interruzione già configurati, l'esecuzione del programma viene sospesa quando il debugger esegue un metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> che restituisce un risultato imprevisto.

Quando si passa il puntatore su un test non superato nella descrizione comando, questa si espande e visualizza informazioni aggiuntive sull'errore, come illustrato nell'immagine seguente. Per passare direttamente a un test non superato, fare doppio clic su di esso nella descrizione comando.

![Informazioni sulla descrizione comando del test non riuscite in Visual Studio](./media/lut-failedmsg.png)

Quando si passa al test non superato, Live Unit Testing visivamente nella firma del metodo i test con:

- passato (indicato da un beaker mezzo pieno insieme a un "✔") verde
- failed (un beaker mezzo pieno insieme a un " 🞩 rosso ")
- non sono coinvolti in Live Unit Testing (un beaker mezzo pieno insieme a un "➖" blu)

I metodi non di test non sono decorati con simboli. L'immagine seguente illustra tutti e quattro i tipi di metodi.

![Metodi di test in Visual Studio con il simbolo di esito positivo o negativo](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnosticare e correggere gli errori di test

Dal test non riuscito è possibile eseguire facilmente il debug del codice del prodotto, apportare modifiche e continuare a sviluppare l'applicazione. Poiché Live Unit Testing in background, non è necessario arrestare e riavviare Live Unit Testing durante il ciclo di debug, modifica e continuazione.

Ad esempio, l'errore di test mostrato nell'immagine precedente è stato causato da un presupposto non corretto nel metodo di test restituito dai caratteri non alfabetici quando vengono passati `true` al <xref:System.Char.IsLower%2A?displayProperty=fullName> metodo . Dopo aver corretto il metodo di test, tutti i test devono essere superati. Non è necessario sospendere o arrestare Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Esplora test

**Esplora test** offre un'interfaccia che consente di eseguire ed eseguire il debug di test e analizzare i risultati dei test. Live Unit Testing si integra con **Esplora test**. Quando Live Unit Testing non è abilitato o è stato arrestato, **Esplora Test** visualizza lo stato degli unit test durante l'ultima esecuzione di un test. Se si apportano modifiche al codice sorgente, è necessario eseguire di nuovo i test. Quando invece è abilitato Live Unit Testing, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è necessario eseguire in modo esplicito gli unit test.

> [!TIP]
> Aprire **Live Unit Testing** selezionando **Test** Windows Esplora test dal menu Visual Studio  >    >   livello superiore.

Nella finestra Esplora **test** è possibile notare che alcuni test sono sfusi. Ad esempio, quando si abilita Live Unit Testing dopo l'apertura  di un progetto salvato in precedenza, la finestra Esplora test ha sfumare tutto, ma il test non riuscito, come illustrato nell'immagine seguente. In questo caso, Live Unit Testing ha eseguito nuovamente il test non riuscito, ma non ha eseguito nuovamente i test riusciti. Questo perché i Live Unit Testing persistenti del test indicano che non sono state apportate modifiche dopo l'ultima esecuzione dei test.

![Test non superato in Esplora test](media/lut-test-explorer.png)

È possibile eseguire di nuovo tutti i  test  visualizzati in dissolvenza selezionando le opzioni Esegui tutto o Esegui dal menu **Esplora** test. In caso contrario, selezionare uno o più test nel **menu** Esplora test, fare clic con il pulsante destro del mouse e quindi scegliere Esegui test selezionati o **Esegui debug** test selezionati dal menu a comparsa.  Quando i test vengono eseguiti, vengono visualizzati nella parte superiore.

Esistono alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Ecco alcune di queste differenze:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati.
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Nella finestra **Esplora test** è possibile scegliere di eseguire più test in parallelo.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing finestra

**Live Unit Testing**, simile a Esplora **test**, fornisce un'interfaccia che consente di eseguire ed eseguire il debug di test e analizzare i risultati dei test. Quando Live Unit Testing abilitata, lo stato degli unit test in **Esplora test** viene aggiornato immediatamente. Non è necessario eseguire in modo esplicito gli unit test. Quando Live Unit Testing è abilitato o **arrestato,** Live Unit Testing lo stato degli unit test all'ultima esecuzione di un test. Dopo il riavvio Live Unit Testing, è necessaria una modifica del codice sorgente per eseguire di nuovo i test.

> [!TIP]
> Iniziare Live Unit Testing selezionando **Test**  >  **Live Unit Testing**  >  **Start** dal menu Visual Studio livello superiore. È anche possibile aprire la **finestra Live Unit Testing** usando **Visualizza**  >  **altro Windows** Live Unit Testing  >  **finestra**.

Nella finestra di dialogo **Live Unit Testing** si noterà che alcuni test sono sfusi. Ad esempio, quando si arresta e  si riavvia Live Unit Testing, la finestra Live Unit Testing dissolvenza di tutti i test, come illustrato nell'immagine seguente. I risultati del test con dissolvenza in uscita indicano che il test non fa parte dell'ultima esecuzione di Live Unit Test. I test vengono eseguiti solo quando viene rilevata una modifica al test o alle dipendenze del test. Se non sono presenti modifiche, evita inutilmente l'esecuzione del test. In questo caso, il risultato del test disattivato è ancora "aggiornato" anche se non fa parte dell'esecuzione più recente.

![Test con dissolvenza in uscita in Esplora test](media/vs-2019/lut-test-explorer.png)

È possibile eseguire di nuovo tutti i test che appaiono sbiaditi apportando una modifica al codice.

Esistono alcune differenze tra l'esecuzione automatica di Live Unit Testing e l'aggiornamento dei risultati dei test e l'esecuzione esplicita di test da **Esplora test**. Ecco alcune di queste differenze:

- Durante l'esecuzione o il debug di test dalla finestra Esplora test vengono eseguiti file binari normali, mentre con Live Unit Testing vengono eseguiti file instrumentati.
- Live Unit Testing non crea un nuovo dominio applicazione per eseguire i test, ma esegue i test dal dominio predefinito. Quando i test vengono eseguiti dalla finestra **Esplora test**, viene invece creato un nuovo dominio applicazione.
- Live Unit Testing esegue i test di ogni assembly di test in modo sequenziale. Nella finestra **Esplora test** è possibile scegliere di eseguire più test in parallelo.
::: moniker-end

## <a name="large-solutions"></a>Soluzioni di grandi dimensioni

Se la soluzione include 10 o più progetti, Visual Studio viene visualizzata la finestra di dialogo seguente quando si:

- avviare Live Unit Testing e non sono presenti dati persistenti
- Selezionare **Strumenti**  >  **Opzioni**  >  **Live Unit Testing**  >  **Elimina dati persistenti**

![Finestra di dialogo di Live Unit Testing per progetti di grandi dimensioni](media/lut-large-project.png)

La finestra di dialogo avvisa che l'esecuzione dinamica di un numero elevato di test in progetti di grandi dimensioni può influire negativamente sulle prestazioni. Se si seleziona **OK**, Live Unit Testing esegue tutti i test della soluzione. Se si seleziona **Annulla**, è possibile selezionare i test da eseguire. La sezione seguente illustra come eseguire questa operazione.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Includere ed escludere progetti e metodi di test

Per le soluzioni con molti progetti di test, è possibile controllare quali progetti e singoli metodi in un progetto partecipano a Live Unit Testing. Se ad esempio una soluzione contiene centinaia di progetti di test, è possibile selezionare un set specifico di progetti di test da includere in Live Unit Testing. Esistono diversi modi per eseguire questa operazione, a seconda che si voglia escludere tutti i test nel progetto o nella soluzione, includere o escludere la maggior parte dei test o escludere singoli test. In Live Unit Testing lo stato di inclusione/esclusione viene salvato come impostazione utente e memorizzato alla chiusura o alla riapertura di una soluzione.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Escludere tutti i test in un progetto o in una soluzione

Per selezionare i singoli progetti negli unit test, eseguire le operazioni seguenti dopo aver avviato Live Unit Testing:

1. Fare clic con il pulsante destro del mouse **sulla soluzione** Esplora soluzioni e **scegliere Live Unit Testing**  >  **Escludi** per escludere l'intera soluzione.
1. Fare clic con il pulsante destro del mouse su ogni progetto di test che si desidera includere nei test **e scegliere** Live Unit Testing  >  **Includi**.

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Escludere singoli test dalla finestra dell'editor di codice

Per includere o escludere singoli metodi di test, è possibile usare la finestra dell'editor del codice. Fare clic con il pulsante destro del mouse sulla firma del metodo di test nella finestra dell'editor di codice e quindi selezionare una delle opzioni seguenti:

- **Live Unit Testing**  >  **Includi \<selected method>**
- **Live Unit Testing**  >  **Escludi \<selected method>**
- **Live Unit Testing**  >  **Escludi tutto ma \<selected method>**

### <a name=&quot;exclude-tests-programmatically&quot;></a>Escludere test a livello di codice

È possibile applicare l'attributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> per evitare a livello di codice che metodi, classi o strutture restituiscano informazioni sul code coverage in Live Unit Testing.

Usare gli attributi seguenti per escludere singoli metodi da Live Unit Testing:

- Per xUnit: `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- Per NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Usare gli attributi seguenti per escludere un intero assembly di test Live Unit Testing:

- Per xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Per NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Per MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Vedi anche

- [Strumenti di test del codice](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing domande frequenti](live-unit-testing-faq.yml)
- [Video di Channel 9: Live Unit Testing in Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
