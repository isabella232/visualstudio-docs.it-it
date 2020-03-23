---
title: Informazioni su come testare il codice con Live Unit Testing
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 748dfc592fbf7a3b9737e9f418362067b92bb8ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594292"
---
# <a name="get-started-with-live-unit-testing"></a>Introduzione a Live Unit Testing

Quando si abilita Live Unit Testing in una soluzione di Visual Studio, vengono illustrati visivamente la copertura di test e lo stato dei test. Live Unit Testing esegue inoltre in modo dinamico i test ogni volta che si modifica il codice e invia immediatamente una notifica quando le modifiche causano l'esito negativo dei test.

Gli unit test in tempo reale possono essere usati per testare soluzioni destinate a .NET Framework o .NET Core.Live Unit Testing can be used to test solutions that target either .NET Framework or .NET Core. In questa esercitazione si apprenderà a usare Live Unit Testing creando una libreria di classi semplice destinata a .NET Standard e verrà creato un progetto MSTest destinato a .NET Core per testarlo.

La soluzione C# completa può essere scaricata dal repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) in GitHub.

## <a name="prerequisites"></a>Prerequisites

Questa esercitazione richiede che sia stato installato Visual Studio Enterprise Edition con il carico di lavoro di sviluppo multipiattaforma .NET Core.This tutorial requires that you've installed Visual Studio Enterprise edition with the **.NET Core cross-platform development** workload.

## <a name="create-the-solution-and-the-class-library-project"></a>Creare la soluzione e il progetto di libreria di classi

Iniziare creando una soluzione di Visual Studio denominata UtilityLibraries costituita da un singolo progetto di libreria di classi .NET Standard, StringLibrary.Start by creating a Visual Studio solution named UtilityLibraries that consists of a single .NET Standard class library project, StringLibrary.

La soluzione è semplicemente un contenitore per uno o più progetti. Per creare una soluzione vuota, aprire Visual Studio ed eseguire le operazioni seguenti:

1. Selezionare **File** > **nuovo** > **progetto** dal menu di Visual Studio di primo livello.

1. Digitare **soluzione** nella casella di ricerca dei modelli e quindi selezionare il modello **Soluzione vuota**.

   ::: moniker range="vs-2017"

   ![Finestra di dialogo Nuovo progetto](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Finire di creare la soluzione.

Dopo aver creato la soluzione, si creerà una libreria di classi denominata StringLibrary che contiene una serie di metodi di estensione per l'utilizzo delle stringhe.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e scegliere **Aggiungi** > **nuovo progetto**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Standard**.

   > [!NOTE]
   > Poiché la libreria è destinata a .NET Standard anziché a una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporta tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Selezionare il modello Libreria di classi **(.NET Standard)** nel riquadro di destra e immettere **StringLibrary** nella casella di testo **Nome,** come illustrato nell'immagine seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto](./media/lut-start/add-project-cs.png)

4. Selezionare **OK** per creare il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **libreria di classi** nella casella di ricerca dei modelli e quindi selezionare il modello **Class Library (.NET Standard)** (Libreria di classi (.NET Standard)). Fare clic su **Avanti**.

   > [!NOTE]
   > Poiché la libreria è destinata a .NET Standard anziché a una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporta tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Assegnare al progetto il nome **StringLibrary**.

4. Fare clic su **Crea** per creare il progetto.

::: moniker-end

5. Nella finestra del codice sostituire il codice esistente con il seguente:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary dispone di tre metodi statici:StringLibrary has three static methods:

   - `StartsWithUpper` restituisce `true` se una stringa inizia con una lettera maiuscola; in caso contrario, restituisce `false`.

   - `StartsWithLower` restituisce `true` se una stringa inizia con una lettera minuscola; in caso contrario, restituisce `false`.

   - `HasEmbeddedSpaces` restituisce `true` se una stringa include uno spazio vuoto; in caso contrario, restituisce `false`.

6. Selezionare **Compila** > **soluzione** dal menu di Visual Studio di primo livello. La compilazione dovrebbe avere esito positivo.

## <a name="create-the-test-project"></a>Creare il progetto di test

Il passaggio successivo consiste nel creare il progetto di unit test per testare la libreria StringLibrary.The next step is to create the unit test project to test the StringLibrary library. Creare gli unit test eseguendo i passaggi seguenti:

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e scegliere **Aggiungi** > **nuovo progetto**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Core**.

   > [!NOTE]
   > Non è necessario scrivere gli unit test nello stesso linguaggio della libreria di classi.

3. Selezionare il modello Progetto unit **test (.NET Core)** nel riquadro destro e immettere **StringLibraryTests** nella casella di testo **Nome,** come illustrato nell'immagine seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto per il progetto di unit test](./media/lut-start/add-unit-test-cs.png)

4. Selezionare **OK** per creare il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **unit test** nella casella di ricerca dei modelli e quindi selezionare il modello **Progetto Unit Test (.NET Core)**. Fare clic su **Avanti**.

3. Denominare il progetto **StringLibraryTests**.

4. Fare clic su **Crea** per creare il progetto.

::: moniker-end

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

5. Il progetto di unit test non può accedere automaticamente alla libreria di classi di cui sta eseguendo il test. L'accesso alla libreria di test viene garantito tramite l'aggiunta di un riferimento al progetto della libreria di classi. A tale scopo, fare `StringLibraryTests` clic con il pulsante destro del mouse sul progetto e **scegliere Aggiungi** > **riferimento**. Nella finestra di dialogo **Gestione riferimenti** verificare che la scheda **Soluzione** sia selezionata e selezionare il progetto StringLibrary, come illustrato nell'immagine seguente.

   ![Finestra di dialogo Gestione riferimenti](./media/lut-start/add-reference.png)

6. Sostituire il codice di unit test boilerplate specificato dal modello con il codice seguente:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Salvare il progetto selezionando l'icona **Salva** sulla barra degli strumenti.

8. Poiché il codice di unit test include alcuni caratteri non ASCII, Visual Studio visualizza la finestra di dialogo seguente per avvertire che alcuni caratteri andranno persi se si salva il file nel formato ASCII predefinito. Scegliere il pulsante **Salva con altra codifica**.

   ![Scegliere una codifica di file](media/lut-start/ascii-encoding.png)

9. Nell'elenco a discesa **Codifica** della finestra di dialogo Opzioni di **salvataggio avanzate,** scegliere **Unicode (UTF-8 senza firma) - Tabella codici 65001**, come illustrato nell'immagine seguente:

   ![Scelta della codifica UTF-8](media/lut-start/utf8-encoding.png)

10. Compilare il progetto di unit test selezionando **Compila** > **compila soluzione** dal menu di Visual Studio di primo livello.

Sono stati creati una libreria di classi e i relativi unit test. Le operazioni preliminari per usare Live Unit Testing sono state completate.

## <a name="enable-live-unit-testing"></a>Abilitare Live Unit Testing

Finora, anche se sono stati scritti i test per la libreria di classi StringLibrary, non sono stati eseguiti. Una volta abilitato, Live Unit Testing li esegue automaticamente. A tal scopo, eseguire le operazioni seguenti:

1. Facoltativamente, selezionare la finestra del codice che contiene il codice per StringLibrary.Optionally, select the code window that contains the code for StringLibrary. Si tratta *di Class1.cs* per un progetto di C , o *Class1.vb* per un progetto di Visual Basic. Questo passaggio consente di controllare visivamente il risultato dei test e l'estensione del code coverage dopo aver abilitato Live Unit Testing.

1. Selezionare **Test** > **Live Unit Testing** > **Start** dal menu di Visual Studio di primo livello.

1. Visual Studio avvia Live Unit Testing, che esegue automaticamente tutti i test.

Al termine dell'esecuzione dei test, in **Esplora test** vengono visualizzati i risultati complessivi e i risultati dei test singoli. Nella finestra del codice vengono anche visualizzati graficamente il code coverage del test e il risultato per i test. Come illustrato nell'immagine seguente, tutti e tre i test sono stati eseguiti correttamente. Viene anche illustrato che i test hanno coperto tutti i percorsi nel metodo `StartsWithUpper` e che tutti i test sono stati eseguiti correttamente. Ciò è indicato dal segno di spunta verde, "✓". Infine, mostra che nessuno degli altri metodi in StringLibrary ha code coverage (che è indicato da una linea blu, "➖").

![Finestra Esplora test e finestra di codice dopo l'avvio di Live Unit Testing](media/lut-start/lut-results-cs.png)

È anche possibile ottenere informazioni più dettagliate sulla copertura e sui risultati dei test selezionando un'icona di code coverage specifica nella finestra del codice. Per esaminare il dettaglio, eseguire le operazioni seguenti:

1. Fare clic sul segno di spunta verde nella riga che include `if (String.IsNullOrWhiteSpace(s))` nel metodo `StartsWithUpper`. Come illustrato nell'immagine seguente, Live Unit Test indica che tre test coprono tale riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione condizionale "if"](media/lut-start/code-coverage-cs1.png)

1. Fare clic sul segno di spunta verde nella riga che include `return Char.IsUpper(s[0])` nel metodo `StartsWithUpper`. Come illustrato nell'immagine seguente, Live Unit Test indica che solo due test coprono tale riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione return](media/lut-start/code-coverage-cs2.png)

Il problema principale che viene rilevato da Live Unit Testing è il code coverage incompleto. Questo problema verrà illustrato nella sezione successiva.

## <a name="expand-test-coverage"></a>Espandere la copertura dei test

In questa sezione verrà illustrato come estendere gli unit test al metodo `StartsWithLower`. Durante questa operazione, Live Unit Testing continuerà a testare il codice.

Per estendere il code coverage al metodo `StartsWithLower`, eseguire le operazioni seguenti:

1. Aggiungere i metodi `TestStartsWithLower` e `TestDoesNotStartWithLower` seguenti al file di codice sorgente del test del progetto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modificare `DirectCallWithNullOrEmpty` il metodo aggiungendo il codice seguente [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) immediatamente dopo la chiamata al metodo.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing esegue automaticamente i test nuovi e modificati quando si modifica il codice sorgente. Come illustrato nell'immagine seguente di **Esplora test,** tutti i test, inclusi i due aggiunti e quello modificato, hanno avuto esito positivo.

   ![Esplora test dopo l'espansione della copertura di testThe Test Explorer after expanding test coverage](media/lut-start/test-dynamic.png)

1. Passare alla finestra che contiene il codice sorgente per la classe StringLibrary. In Live Unit Testing ora viene visualizzato il code coverage esteso al metodo `StartsWithLower`.

    ![Code coverage per il metodo StartsWithLower](media/lut-start/lut-extended-cs.png)

In alcuni casi, i test riusciti in **Esplora test** potrebbero essere disattivati. Ciò indica che un test è attualmente in esecuzione o che il test non è stato eseguito di nuovo perché non sono state apportate modifiche al codice che potrebbero influire sul test dall'ultima esecuzione.

Fino a questo punto, tutti i test hanno avuto esito positivo. Nella sezione successiva esamineremo come gestire l'esito negativo dei test.

## <a name="handle-a-test-failure"></a>Gestire i test non riusciti

In questa sezione verrà illustrato come usare Live Unit Testing per identificare e risolvere i problemi relativi ai test con esito negativo. A questo scopo sarà necessario espandere la copertura dei test al metodo `HasEmbeddedSpaces`.

1. Aggiungere il metodo seguente al file di test:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Quando viene eseguito il test, Live `TestHasEmbeddedSpaces` Unit Testing indica che il metodo non è riuscito, come illustrato nell'immagine seguente:

   ![Esplora test che segnala un test non riuscito](media/lut-start/test-failure.png)

1. Selezionare la finestra in cui viene visualizzato il codice della libreria. Live Unit Testing ha ampliato il code coverage per il `HasEmbeddedSpaces` metodo. Viene segnalato anche il test con esito negativo tramite l'aggiunta di una "🞩" rossa in corrispondenza delle righe per le quali i test non sono stati superati.

1. Passare il mouse sulla riga con la firma del metodo `HasEmbeddedSpaces`. Live Unit Testing visualizza una descrizione comando che indica che il metodo è coperto da un test, come illustrato nell'immagine seguente:Live Unit Testing displays a tooltip that reports that the method is covered by one test, as the following image shows:

   ![Informazioni su Live Unit Testing su un test non riuscito](media/lut-start/test-failure-info-cs.png)

1. Selezionare il test non riuscito **TestHasEmbeddedSpaces**. Live Unit Testing offre numerose opzioni, ad esempio l'esecuzione di tutti i test, l'esecuzione dei test selezionati, il debug di tutti i test e il debug dei test selezionati, come illustrato nell'immagine seguente:

   ![Opzioni di Live Unit Testing per un test non superato](media/lut-start/test-failure-options.png)

1. Selezionare **Debug Selected** (Debug selezionato) per eseguire il debug del test non riuscito.

1. Visual Studio esegue il test in modalità di debug.

   Il test assegna ogni stringa in una `phrase` matrice a `HasEmbeddedSpaces` una variabile denominata e la passa al metodo. L'esecuzione del programma viene sospesa e viene richiamato il debugger la prima volta in cui l'espressione di asserzione è `false`. La finestra di dialogo di [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) eccezione risultante dal valore imprevisto nella chiamata al metodo è illustrata nell'immagine seguente.

   ![Finestra di dialogo di eccezione di Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Inoltre, tutti gli strumenti di debug forniti da Visual Studio sono disponibili per risolvere i problemi relativi al test non riuscito, come illustrato nell'immagine seguente:In addition, all of the debugging tools that Visual Studio provides are available to help us troubleshoot our failed test, as the following image shows:

   ![Strumenti di debug di Visual StudioVisual Studio debugging tools](media/lut-start/debugging-tools-cs.png)

   Si noti che nella finestra **Auto** il valore della variabile `phrase` è "Name\tDescription", che è il secondo elemento della matrice. Il metodo di test prevede che `HasEmbeddedSpaces` restituisca `true` quando viene passata questa stringa; in questo caso restituisce invece `false`. Evidentemente, non riconosce "\t", il carattere di tabulazione, come uno spazio incorporato.

1. Selezionare**Debug Continue (Continua** **di eseguire** > il debug) premere **F5**oppure fare clic sul pulsante **Continue (Continua)** sulla barra degli strumenti per continuare l'esecuzione del programma di test. Dal momento che si è verificata un'eccezione non gestita, il test viene terminato.
In questo modo vengono specificate informazioni sufficienti per un'analisi preliminare del bug. `TestHasEmbeddedSpaces`, la routine di test, ha generato un presupposto errato, oppure `HasEmbeddedSpaces` non riconosce correttamente tutti gli spazi incorporati.

1. Per diagnosticare e correggere il `StringLibrary.HasEmbeddedSpaces` problema, iniziare con il metodo. Esaminare il confronto nel metodo `HasEmbeddedSpaces`. Lo spazio incorporato viene considerato come U+0020. Tuttavia, lo standard Unicode include altri caratteri spazio. Ne consegue che nel codice della libreria è stato eseguito un test per gli spazi vuoti errato.

1. Sostituire il confronto delle uguaglianze con una chiamata al metodo <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing esegue automaticamente il metodo di test non riuscito e aggiorna i risultati nella finestra del codice e in **Esplora test,** come illustrato nell'immagine seguente:

    ![Test HasEmbeddedSpaces riuscito](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Vedere anche

- [Live Unit Testing con Visual Studio 2017](live-unit-testing.md)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
