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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594292"
---
# <a name="get-started-with-live-unit-testing"></a>Introduzione a Live Unit Testing

Quando si Abilita Live Unit Testing in una soluzione di Visual Studio, viene illustrato visivamente il code coverage del test e lo stato dei test. Live Unit Testing esegue anche in modo dinamico i test ogni volta che si modifica il codice e invia immediatamente una notifica quando le modifiche provocano l'esito negativo dei test.

Live Unit Testing può essere usato per testare soluzioni che hanno come destinazione .NET Framework o .NET Core. In questa esercitazione si apprenderà come usare Live Unit Testing creando una libreria di classi semplice destinata .NET Standard e verrà creato un progetto MSTest destinato a .NET Core per testarlo.

La soluzione C# completa può essere scaricata dal repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) in GitHub.

## <a name="prerequisites"></a>Prerequisiti

Per questa esercitazione è necessario aver installato Visual Studio Enterprise Edition con il carico di lavoro **sviluppo multipiattaforma .NET Core** .

## <a name="create-the-solution-and-the-class-library-project"></a>Creare la soluzione e il progetto di libreria di classi

Per iniziare, creare una soluzione di Visual Studio denominata UtilityLibraries costituita da un singolo progetto libreria di classi .NET Standard, StringLibrary.

La soluzione è semplicemente un contenitore per uno o più progetti. Per creare una soluzione vuota, aprire Visual Studio ed eseguire le operazioni seguenti:

1. Selezionare **File** > **Nuovo** > **Progetto** dal menu di primo livello di Visual Studio.

1. Digitare **soluzione** nella casella di ricerca dei modelli e quindi selezionare il modello **Soluzione vuota**.

   ::: moniker range="vs-2017"

   ![Finestra di dialogo Nuovo progetto](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Finire di creare la soluzione.

Ora che è stata creata la soluzione, verrà creata una libreria di classi denominata StringLibrary che contiene una serie di metodi di estensione per l'uso delle stringhe.

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e scegliere **Aggiungi** > **nuovo progetto**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Standard**.

   > [!NOTE]
   > Poiché la libreria è destinata .NET Standard anziché una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporti tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Selezionare il modello **libreria di classi (.NET standard)** nel riquadro di destra e immettere **StringLibrary** nella casella di testo **nome** , come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto](./media/lut-start/add-project-cs.png)

4. Selezionare **OK** per creare il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **libreria di classi** nella casella di ricerca dei modelli e quindi selezionare il modello **Class Library (.NET Standard)** (Libreria di classi (.NET Standard)). Scegliere **Avanti**.

   > [!NOTE]
   > Poiché la libreria è destinata .NET Standard anziché una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione di .NET che supporti tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Denominare il progetto **StringLibrary**.

4. Fare clic su **Crea** per creare il progetto.

::: moniker-end

5. Nella finestra del codice sostituire il codice esistente con il seguente:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary dispone di tre metodi statici:

   - `StartsWithUpper` restituisce `true` se una stringa inizia con una lettera maiuscola; in caso contrario, restituisce `false`.

   - `StartsWithLower` restituisce `true` se una stringa inizia con una lettera minuscola; in caso contrario, restituisce `false`.

   - `HasEmbeddedSpaces` restituisce `true` se una stringa include uno spazio vuoto; in caso contrario, restituisce `false`.

6. Selezionare **Compila** > **Compila soluzione** dal menu di primo livello di Visual Studio. La compilazione dovrebbe avere esito positivo.

## <a name="create-the-test-project"></a>Creare il progetto di test

Il passaggio successivo consiste nel creare il progetto unit test per testare la libreria StringLibrary. Creare gli unit test eseguendo i passaggi seguenti:

1. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e scegliere **Aggiungi** > **nuovo progetto**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Core**.

   > [!NOTE]
   > Non è necessario scrivere gli unit test nello stesso linguaggio della libreria di classi.

3. Selezionare il modello **progetto unit test (.NET Core)** nel riquadro di destra e immettere **StringLibraryTests** nella casella di testo **nome** , come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto per il progetto di unit test](./media/lut-start/add-unit-test-cs.png)

4. Selezionare **OK** per creare il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **unit test** nella casella di ricerca dei modelli e quindi selezionare il modello **Progetto Unit Test (.NET Core)** . Scegliere **Avanti**.

3. Denominare il progetto **StringLibraryTests**.

4. Fare clic su **Crea** per creare il progetto.

::: moniker-end

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

5. Il progetto di unit test non può accedere automaticamente alla libreria di classi di cui sta eseguendo il test. L'accesso alla libreria di test viene garantito tramite l'aggiunta di un riferimento al progetto della libreria di classi. A questo scopo, fare clic con il pulsante destro del mouse sul progetto `StringLibraryTests` e selezionare **Aggiungi** > **Riferimento**. Nella finestra di dialogo **Gestione riferimenti** verificare che la scheda **soluzione** sia selezionata e selezionare il progetto StringLibrary, come illustrato nella figura seguente.

   ![Finestra di dialogo Gestione riferimenti](./media/lut-start/add-reference.png)

6. Sostituire il codice di unit test boilerplate specificato dal modello con il codice seguente:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Salvare il progetto selezionando l'icona **Salva** sulla barra degli strumenti.

8. Poiché il codice unit test include alcuni caratteri non ASCII, Visual Studio Visualizza la finestra di dialogo seguente per avvisare che alcuni caratteri andranno perduti se si salva il file nel formato ASCII predefinito. Scegliere il pulsante **Salva con altra codifica**.

   ![Scegliere una codifica di file](media/lut-start/ascii-encoding.png)

9. Nell'elenco a discesa **codifica** della finestra di dialogo **Opzioni di salvataggio avanzate** scegliere **Unicode (UTF-8 senza firma)-tabella codici 65001**, come illustrato nella figura seguente:

   ![Scelta della codifica UTF-8](media/lut-start/utf8-encoding.png)

10. Compilare il progetto di unit test scegliendo **Compila** > **Ricompila soluzione** dal menu principale di Visual Studio.

Sono stati creati una libreria di classi e i relativi unit test. Le operazioni preliminari per usare Live Unit Testing sono state completate.

## <a name="enable-live-unit-testing"></a>Abilitare Live Unit Testing

Fino ad ora, anche se sono stati scritti i test per la libreria di classi StringLibrary, non sono stati eseguiti. Una volta abilitato, Live Unit Testing li esegue automaticamente. A tale scopo, eseguire le operazioni seguenti:

1. Facoltativamente, selezionare la finestra del codice che contiene il codice per StringLibrary. Si tratta di *Class1.cs* per un progetto C# o di *Class1.vb* per un progetto di Visual Basic. Questo passaggio consente di esaminare visivamente il risultato dei test e la portata del code coverage dopo aver abilitato Live Unit Testing.

1. Selezionare **Test** > **Live Unit Testing** > **Avvia** dal menu di primo livello di Visual Studio.

1. Visual Studio avvia Live Unit Testing, che esegue automaticamente tutti i test.

Al termine dell'esecuzione dei test, in **Esplora test** vengono visualizzati i risultati complessivi e i risultati dei test singoli. Nella finestra del codice vengono anche visualizzati graficamente il code coverage del test e il risultato per i test. Come illustrato nell'immagine seguente, tutti e tre i test sono stati eseguiti correttamente. Viene anche illustrato che i test hanno coperto tutti i percorsi nel metodo `StartsWithUpper` e che tutti i test sono stati eseguiti correttamente. Ciò è indicato dal segno di spunta verde, "✓". Infine, Mostra che nessuno degli altri metodi di StringLibrary ha code coverage (che è indicato da una linea blu, "➖").

![Finestra Esplora test e finestra di codice dopo l'avvio di Live Unit Testing](media/lut-start/lut-results-cs.png)

È anche possibile ottenere informazioni più dettagliate sulla copertura e sui risultati dei test selezionando un'icona di code coverage specifica nella finestra del codice. Per esaminare il dettaglio, eseguire le operazioni seguenti:

1. Fare clic sul segno di spunta verde nella riga che include `if (String.IsNullOrWhiteSpace(s))` nel metodo `StartsWithUpper`. Come illustrato nell'immagine seguente, Live Unit Testing indica che tre test coprono la riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione condizionale "if"](media/lut-start/code-coverage-cs1.png)

1. Fare clic sul segno di spunta verde nella riga che include `return Char.IsUpper(s[0])` nel metodo `StartsWithUpper`. Come illustrato nell'immagine seguente, Live Unit Testing indica che solo due test coprono la riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione return](media/lut-start/code-coverage-cs2.png)

Il problema principale che viene rilevato da Live Unit Testing è il code coverage incompleto. Questo problema verrà illustrato nella sezione successiva.

## <a name="expand-test-coverage"></a>Espandere la copertura dei test

In questa sezione verrà illustrato come estendere gli unit test al metodo `StartsWithLower`. Durante questa operazione, Live Unit Testing continuerà a testare il codice.

Per estendere il code coverage al metodo `StartsWithLower`, eseguire le operazioni seguenti:

1. Aggiungere i metodi `TestStartsWithLower` e `TestDoesNotStartWithLower` seguenti al file di codice sorgente del test del progetto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modificare il metodo `DirectCallWithNullOrEmpty` aggiungendo il codice seguente immediatamente dopo la chiamata al metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse).

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing esegue automaticamente i test nuovi e modificati quando si modifica il codice sorgente. Come illustrato nell'immagine seguente di **Esplora test** , tutti i test, inclusi i due elementi aggiunti e quelli modificati, hanno avuto esito positivo.

   ![Esplora test dopo l'espansione del code coverage dei test](media/lut-start/test-dynamic.png)

1. Passare alla finestra che contiene il codice sorgente per la classe StringLibrary. In Live Unit Testing ora viene visualizzato il code coverage esteso al metodo `StartsWithLower`.

    ![Code coverage per il metodo StartsWithLower](media/lut-start/lut-extended-cs.png)

In alcuni casi, i test riusciti in **Esplora test** possono essere visualizzati in grigio. Che indica che un test è attualmente in esecuzione o che il test non è stato eseguito di nuovo perché non sono state apportate modifiche al codice che influiscano sul test dopo l'ultima esecuzione.

Fino a questo punto, tutti i test hanno avuto esito positivo. Nella sezione successiva esamineremo come gestire l'esito negativo dei test.

## <a name="handle-a-test-failure"></a>Gestire i test non riusciti

In questa sezione verrà illustrato come usare Live Unit Testing per identificare e risolvere i problemi relativi ai test con esito negativo. A questo scopo sarà necessario espandere la copertura dei test al metodo `HasEmbeddedSpaces`.

1. Aggiungere il metodo seguente al file di test:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Quando il test viene eseguito, Live Unit Testing indica che il metodo `TestHasEmbeddedSpaces` ha avuto esito negativo, come illustrato nella figura seguente:

   ![Esplora test che segnala un test non superato](media/lut-start/test-failure.png)

1. Selezionare la finestra in cui viene visualizzato il codice della libreria. Live Unit Testing ha espanso code coverage al metodo `HasEmbeddedSpaces`. Viene segnalato anche il test con esito negativo tramite l'aggiunta di una "🞩" rossa in corrispondenza delle righe per le quali i test non sono stati superati.

1. Passare il mouse sulla riga con la firma del metodo `HasEmbeddedSpaces`. Live Unit Testing Visualizza una descrizione comando che indica che il metodo è coperto da un test, come illustrato nella figura seguente:

   ![Live Unit Testing informazioni su un test non superato](media/lut-start/test-failure-info-cs.png)

1. Selezionare il test non riuscito **TestHasEmbeddedSpaces**. Live Unit Testing offre diverse opzioni, ad esempio l'esecuzione di tutti i test, l'esecuzione dei test selezionati, il debug di tutti i test e il debug dei test selezionati, come illustrato nella figura seguente:

   ![Opzioni di Live Unit Testing per un test non superato](media/lut-start/test-failure-options.png)

1. Selezionare **Debug Selected** (Debug selezionato) per eseguire il debug del test non riuscito.

1. Visual Studio esegue il test in modalità di debug.

   Il test assegna ogni stringa in una matrice a una variabile denominata `phrase` e la passa al metodo `HasEmbeddedSpaces`. L'esecuzione del programma viene sospesa e viene richiamato il debugger la prima volta in cui l'espressione di asserzione è `false`. Nella figura seguente è illustrata la finestra di dialogo di eccezione risultante dal valore imprevisto nella chiamata al metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) .

   ![Finestra di dialogo Live Unit Testing eccezione](media/lut-start/exception-dialog-cs.png)

   Inoltre, sono disponibili tutti gli strumenti di debug forniti da Visual Studio per consentire la risoluzione dei problemi del test non superato, come illustrato nella figura seguente:

   ![Strumenti di debug di Visual Studio](media/lut-start/debugging-tools-cs.png)

   Si noti che nella finestra **Auto** il valore della variabile `phrase` è "Name\tDescription", che è il secondo elemento della matrice. Il metodo di test prevede che `HasEmbeddedSpaces` restituisca `true` quando viene passata questa stringa; in questo caso restituisce invece `false`. Evidentemente, non riconosce "\t", il carattere di tabulazione, come uno spazio incorporato.

1. Selezionare **Debug** > **Continua**, premere **F5** o fare clic sul pulsante **Continua** sulla barra degli strumenti per continuare a eseguire il programma di test. Dal momento che si è verificata un'eccezione non gestita, il test viene terminato.
In questo modo vengono specificate informazioni sufficienti per un'analisi preliminare del bug. `TestHasEmbeddedSpaces`, la routine di test, ha generato un presupposto errato, oppure `HasEmbeddedSpaces` non riconosce correttamente tutti gli spazi incorporati.

1. Per diagnosticare e correggere il problema, iniziare con il metodo `StringLibrary.HasEmbeddedSpaces`. Esaminare il confronto nel metodo `HasEmbeddedSpaces`. Lo spazio incorporato viene considerato come U+0020. Tuttavia, lo standard Unicode include altri caratteri spazio. Ne consegue che nel codice della libreria è stato eseguito un test per gli spazi vuoti errato.

1. Sostituire il confronto delle uguaglianze con una chiamata al metodo <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing esegue automaticamente il metodo di test non superato e aggiorna i risultati nella finestra del codice e in **Esplora test**, come illustrato nella figura seguente:

    ![Test HasEmbeddedSpaces riuscito](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Vedere anche

- [Live Unit Testing in Visual Studio](live-unit-testing.md)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.md)
