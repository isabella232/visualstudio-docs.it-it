---
title: Informazioni su come testare il codice con Live Unit Testing
description: Informazioni su come Live Unit Testing creare una semplice libreria di classi destinata a .NET Standard e creare un progetto MSTest destinato a .NET Core per testarlo.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- dotnet
ms.openlocfilehash: 7a1f02972ced010110f7ff43c87c342c956c35623b49b49a0ce0b4ee173e6c2d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121227245"
---
# <a name="get-started-with-live-unit-testing"></a>Introduzione a Live Unit Testing

Quando si abilita Live Unit Testing in una soluzione Visual Studio, viene illustrato visivamente il code coverage dei test e lo stato dei test. Live Unit Testing inoltre in modo dinamico esegue i test ogni volta che si modifica il codice e invia immediatamente una notifica quando le modifiche causano l'esito negativo dei test.

Live Unit Testing può essere usato per testare soluzioni che hanno come destinazione .NET Framework o .NET Core. In questa esercitazione si apprenderà come usare Live Unit Testing creando una semplice libreria di classi destinata a .NET Standard e si creerà un progetto MSTest destinato a .NET Core per testarlo.

La soluzione C# completa può essere scaricata dal repository [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) in GitHub.

## <a name="prerequisites"></a>Prerequisiti

Per questa esercitazione è necessario aver installato l'edizione Visual Studio Enterprise con il carico di lavoro **Sviluppo multipiattaforma .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Creare la soluzione e il progetto di libreria di classi

Iniziare creando una soluzione Visual Studio denominata UtilityLibraries costituita da un singolo progetto .NET Standard libreria di classi, StringLibrary.

La soluzione è semplicemente un contenitore per uno o più progetti. Per creare una soluzione vuota, aprire Visual Studio ed eseguire le operazioni seguenti:

1. Selezionare **File**  >  **Nuovo**  >  **Project** dal menu di Visual Studio di primo livello.

1. Digitare **soluzione** nella casella di ricerca dei modelli e quindi selezionare il modello **Soluzione vuota**. Assegnare al progetto **il nome UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Finestra di dialogo Nuovo progetto](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Finire di creare la soluzione.

Dopo aver creato la soluzione, si creerà una libreria di classi denominata StringLibrary che contiene diversi metodi di estensione per l'uso delle stringhe.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e  >  **scegliere Aggiungi nuovo Project**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Standard**.

   > [!NOTE]
   > Poiché la libreria è .NET Standard anziché una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione .NET che supporta tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Selezionare il **modello Libreria di classi (.NET Standard)** nel riquadro destro e immettere **StringLibrary** nella casella **di** testo Nome, come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto](./media/lut-start/add-project-cs.png)

4. Selezionare **OK** per creare il progetto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **libreria di classi** nella casella di ricerca dei modelli e quindi selezionare il modello **Class Library (.NET Standard)** (Libreria di classi (.NET Standard)). Fare clic su **Avanti**.

   > [!NOTE]
   > Poiché la libreria è .NET Standard anziché una particolare implementazione di .NET, può essere chiamata da qualsiasi implementazione .NET che supporta tale versione di .NET Standard. Per altre informazioni, vedere [.NET Standard](/dotnet/standard/net-standard).

3. Assegnare al progetto il **nome StringLibrary**.

4. Fare clic su **Crea** per creare il progetto.

::: moniker-end

5. Sostituire tutto il codice esistente nell'editor di codice con il codice seguente:

   ```csharp
   using System;

   namespace UtilityLibraries
   {
       public static class StringLibrary
       {
           public static bool StartsWithUpper(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsUpper(s[0]);
           }

           public static bool StartsWithLower(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsLower(s[0]);
           }

           public static bool HasEmbeddedSpaces(this string s)
           {
               foreach (var ch in s.Trim())
               {
                   if (ch == ' ')
                       return true;
               }
               return false;
           }
       }
   }
   ```

   StringLibrary ha tre metodi statici:

   - `StartsWithUpper` restituisce `true` se una stringa inizia con una lettera maiuscola; in caso contrario, restituisce `false`.

   - `StartsWithLower` restituisce `true` se una stringa inizia con una lettera minuscola; in caso contrario, restituisce `false`.

   - `HasEmbeddedSpaces` restituisce `true` se una stringa include uno spazio vuoto; in caso contrario, restituisce `false`.

6. Selezionare **Build**  >  **Build Solution (Compila** soluzione) dal menu di Visual Studio di primo livello. La compilazione dovrebbe avere esito positivo.

## <a name="create-the-test-project"></a>Creare il progetto di test

Il passaggio successivo consiste nel creare il unit test per testare la libreria StringLibrary. Creare gli unit test eseguendo i passaggi seguenti:

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione UtilityLibraries e  >  **scegliere Aggiungi nuovo Project**.

::: moniker range="vs-2017"

2. Nella finestra di dialogo **Aggiungi nuovo progetto** selezionare il nodo C# e quindi **.NET Core**.

   > [!NOTE]
   > Non è necessario scrivere gli unit test nello stesso linguaggio della libreria di classi.

3. Selezionare il **modello unit test Project (.NET Core)** nel riquadro destro e immettere **StringLibraryTests** nella casella di testo **Nome,** come illustrato nella figura seguente:

   ![Finestra di dialogo Aggiungi nuovo progetto per il progetto di unit test](./media/lut-start/add-unit-test-cs.png)

4. Selezionare **OK** per creare il progetto.

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digitare **unit test** nella casella di ricerca del modello, selezionare **C#** come linguaggio e quindi selezionare il modello unit **test Project** per .NET Core. Fare clic su **Avanti**.

   > [!NOTE]
   > A partire da Visual Studio 2019 versione 16.9, il nome del modello di progetto MSTest è stato modificato da **MSTest Unit Test Project (.NET Core)** a **Unit Test Project**.

3. Assegnare al progetto il **nome StringLibraryTests** e fare clic **su Avanti.**

4. Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**

   > [!NOTE]
   > Questa esercitazione introduttiva usa Live Unit Testing con il framework di test MSTest. È possibile usare anche i framework di test xUnit e NUnit.

::: moniker-end

5. Il progetto di unit test non può accedere automaticamente alla libreria di classi di cui sta eseguendo il test. L'accesso alla libreria di test viene garantito tramite l'aggiunta di un riferimento al progetto della libreria di classi. A tale scopo, fare clic con il pulsante destro del `StringLibraryTests` mouse sul progetto e scegliere **Aggiungi**  >  **riferimento.** Nella finestra **di dialogo Gestione** riferimenti verificare che la scheda **Soluzione** sia selezionata e selezionare il progetto StringLibrary, come illustrato nella figura seguente.

   ![Finestra di dialogo Gestione riferimenti](./media/lut-start/add-reference.png)

6. Sostituire il codice di unit test boilerplate specificato dal modello con il codice seguente:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using UtilityLibraries;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestStartsWithUpper()
           {
               // Tests that we expect to return true.
               string[] words = { "Alphabet", "Zebra", "ABC", "Αθήνα", "Москва" };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsTrue(result,
                                 $"Expected for '{word}': true; Actual: {result}");
               }
           }

           [TestMethod]
           public void TestDoesNotStartWithUpper()
           {
               // Tests that we expect to return false.
               string[] words = { "alphabet", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                                  "1234", ".", ";", " " };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsFalse(result,
                                  $"Expected for '{word}': false; Actual: {result}");
               }
           }

           [TestMethod]
           public void DirectCallWithNullOrEmpty()
           {
               // Tests that we expect to return false.
               string[] words = { String.Empty, null };
               foreach (var word in words)
               {
                   bool result = StringLibrary.StartsWithUpper(word);
                   Assert.IsFalse(result,
                                  $"Expected for '{(word == null ? "<null>" : word)}': " +
                                  $"false; Actual: {result}");
               }
           }
       }
   }
   ```

7. Salvare il progetto selezionando l'icona **Salva** sulla barra degli strumenti.

   Poiché il unit test include alcuni caratteri non ASCII, verrà visualizzata la finestra di dialogo seguente per avvisare che alcuni caratteri andranno persi se si salva il file nel formato ASCII predefinito.

8. Scegliere il pulsante **Salva con altra codifica**.

   ![Scegliere una codifica di file](media/lut-start/ascii-encoding.png)

9. **Nell'elenco** a discesa Codifica  della finestra di dialogo Opzioni di salvataggio avanzate scegliere **Unicode (UTF-8 senza firma) - Tabella codici 65001,** come illustrato nella figura seguente:

   ![Scelta della codifica UTF-8](media/lut-start/utf8-encoding.png)

10. Compilare unit test progetto selezionando **Compila**  >  **ricompila soluzione** dal menu di Visual Studio di primo livello.

Sono stati creati una libreria di classi e i relativi unit test. Le operazioni preliminari per usare Live Unit Testing sono state completate.

## <a name="enable-live-unit-testing"></a>Abilitare Live Unit Testing

Fino a questo punto, anche se sono stati scritti i test per la libreria di classi StringLibrary, non sono stati eseguiti. Una volta abilitato, Live Unit Testing li esegue automaticamente. A tal scopo, eseguire le operazioni seguenti:

1. Facoltativamente, selezionare la finestra dell'editor di codice che contiene il codice per StringLibrary. Si tratta di *Class1.cs per* un progetto C# o *Class1.vb* per un Visual Basic progetto. Questo passaggio consente di esaminare visivamente il risultato dei test e l'entità del code coverage dopo aver abilitato Live Unit Testing.

1. Selezionare **Test**  >  **Live Unit Testing**  >  **Start** (Avvia) dal menu di Visual Studio di primo livello.

1. Visual Studio avvia Live Unit Testing, che esegue automaticamente tutti i test.

::: moniker range="vs-2017"
Al termine dell'esecuzione dei test, in **Esplora test** vengono visualizzati i risultati complessivi e i risultati dei test singoli. Inoltre, la finestra dell'editor di codice visualizza graficamente sia l'code coverage test che il risultato per i test. Come illustrato nella figura seguente, tutti e tre i test sono stati eseguiti correttamente. Viene anche illustrato che i test hanno coperto tutti i percorsi nel metodo `StartsWithUpper` e che tutti i test sono stati eseguiti correttamente. Ciò è indicato dal segno di spunta verde, "✓". Infine, mostra che nessuno degli altri metodi in StringLibrary ha code coverage (indicata da una riga blu, "➖").

![Finestra Esplora test e editor di codice dopo l'avvio di Live Unit Testing](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019&quot;
Al termine dell'esecuzione dei test, **Live Unit Testing** i risultati complessivi e i risultati dei singoli test. Inoltre, la finestra dell'editor di codice visualizza graficamente sia l'code coverage test che il risultato per i test. Come illustrato nella figura seguente, tutti e tre i test sono stati eseguiti correttamente. Viene anche illustrato che i test hanno coperto tutti i percorsi nel metodo `StartsWithUpper` e che tutti i test sono stati eseguiti correttamente. Ciò è indicato dal segno di spunta verde, &quot;✓&quot;. Infine, mostra che nessuno degli altri metodi in StringLibrary ha code coverage (indicata da una riga blu, &quot;➖").

![Finestra Esplora test in tempo reale e editor di codice dopo l'avvio di Live Unit Testing](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

È anche possibile ottenere informazioni più dettagliate sul code coverage e sui risultati dei test selezionando un'icona di code coverage nella finestra dell'editor di codice. Per esaminare il dettaglio, eseguire le operazioni seguenti:

1. Fare clic sul segno di spunta verde nella riga che include `if (String.IsNullOrWhiteSpace(s))` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing indica che tre test coprono tale riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione condizionale "if"](media/lut-start/code-coverage-cs1.png)

1. Fare clic sul segno di spunta verde nella riga che include `return Char.IsUpper(s[0])` nel metodo `StartsWithUpper`. Come illustrato nella figura seguente, Live Unit Testing che solo due test coprono tale riga di codice e che tutti sono stati eseguiti correttamente.

   ![Code coverage per l'istruzione return](media/lut-start/code-coverage-cs2.png)

Il problema principale che viene rilevato da Live Unit Testing è il code coverage incompleto. Questo problema verrà illustrato nella sezione successiva.

## <a name="expand-test-coverage"></a>Espandere la copertura dei test

In questa sezione verrà illustrato come estendere gli unit test al metodo `StartsWithLower`. Durante questa operazione, Live Unit Testing continuerà a testare il codice.

Per estendere il code coverage al metodo `StartsWithLower`, eseguire le operazioni seguenti:

1. Aggiungere i metodi `TestStartsWithLower` e `TestDoesNotStartWithLower` seguenti al file di codice sorgente del test del progetto:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. Modificare il `DirectCallWithNullOrEmpty` metodo aggiungendo il codice seguente immediatamente dopo la chiamata al metodo [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) .

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing esegue automaticamente i test nuovi e modificati quando si modifica il codice sorgente. Come illustrato nella figura seguente, tutti i test, inclusi i due aggiunti e quello modificato, hanno avuto esito positivo.

   ::: moniker range="vs-2017"
   ![Esplora test dopo l'espansione del code coverage dei test](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Esplora test live dopo l'espansione del code coverage dei test](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Passare alla finestra che contiene il codice sorgente per la classe StringLibrary. In Live Unit Testing ora viene visualizzato il code coverage esteso al metodo `StartsWithLower`.

    ![Code coverage per il metodo StartsWithLower](media/lut-start/lut-extended-cs.png)

In alcuni casi, i test riusciti in **Esplora test** potrebbero essere disattivati. Ciò indica che un test è attualmente in esecuzione o che il test non è stato eseguito di nuovo perché non sono state apportate modifiche al codice che potrebbero influire sul test dopo l'ultima esecuzione.

Fino a questo punto, tutti i test hanno avuto esito positivo. Nella sezione successiva esamineremo come gestire l'esito negativo dei test.

## <a name="handle-a-test-failure"></a>Gestire i test non riusciti

In questa sezione verrà illustrato come usare Live Unit Testing per identificare e risolvere i problemi relativi ai test con esito negativo. A questo scopo sarà necessario espandere la copertura dei test al metodo `HasEmbeddedSpaces`.

1. Aggiungere il metodo seguente al file di test:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

1. Quando il test viene eseguito, Live Unit Testing indica che il metodo ha avuto esito `TestHasEmbeddedSpaces` negativo, come illustrato nella figura seguente:

   ::: moniker range="vs-2017"
   ![Esplora test che segnala un test non superato](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Esplora test live che segnala un test non superato](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Selezionare la finestra in cui viene visualizzato il codice della libreria. Live Unit Testing ha espanso code coverage al `HasEmbeddedSpaces` metodo . Viene segnalato anche il test con esito negativo tramite l'aggiunta di una "🞩" rossa in corrispondenza delle righe per le quali i test non sono stati superati.

1. Passare il mouse sulla riga con la firma del metodo `HasEmbeddedSpaces`. Live Unit Testing una descrizione comando che segnala che il metodo è coperto da un test, come illustrato nella figura seguente:

   ![Live Unit Testing informazioni su un test non superato](media/lut-start/test-failure-info-cs.png)

1. Selezionare il test non riuscito **TestHasEmbeddedSpaces**. Live Unit Testing offre alcune opzioni, ad esempio l'esecuzione di tutti i test e il debug di tutti i test, come illustrato nella figura seguente:

   ::: moniker range="vs-2017"
   ![Live Unit Testing opzioni per un test non superato](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Unit Testing opzioni per un test non superato](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Selezionare **Debug tutto per** eseguire il debug del test non superato.

1. Visual Studio esegue il test in modalità di debug.

   Il test assegna ogni stringa in una matrice a una variabile denominata `phrase` e la passa al metodo `HasEmbeddedSpaces` . L'esecuzione del programma viene sospesa e viene richiamato il debugger la prima volta in cui l'espressione di asserzione è `false`. La finestra di dialogo dell'eccezione che risulta dal valore imprevisto nella chiamata [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) al metodo è illustrata nella figura seguente.

   ![Live Unit Testing finestra di dialogo delle eccezioni](media/lut-start/exception-dialog-cs.png)

   Sono inoltre disponibili tutti gli strumenti di debug Visual Studio per risolvere i problemi del test non superato, come illustrato nella figura seguente:

   ![Visual Studio strumenti di debug](media/lut-start/debugging-tools-cs.png)

   Si noti che nella finestra **Auto** il valore della variabile `phrase` è "Name\tDescription", che è il secondo elemento della matrice. Il metodo di test prevede che `HasEmbeddedSpaces` restituisca `true` quando viene passata questa stringa; in questo caso restituisce invece `false`. Evidentemente, non riconosce "\t", il carattere di tabulazione, come uno spazio incorporato.

1. Selezionare **Debug** continua , premere F5 o fare clic sul pulsante Continua sulla barra degli strumenti  >  per continuare l'esecuzione del programma di test.   Dal momento che si è verificata un'eccezione non gestita, il test viene terminato.
In questo modo vengono specificate informazioni sufficienti per un'analisi preliminare del bug. `TestHasEmbeddedSpaces`, la routine di test, ha generato un presupposto errato, oppure `HasEmbeddedSpaces` non riconosce correttamente tutti gli spazi incorporati.

1. Per diagnosticare e correggere il problema, iniziare con il `StringLibrary.HasEmbeddedSpaces` metodo . Esaminare il confronto nel metodo `HasEmbeddedSpaces`. Lo spazio incorporato viene considerato come U+0020. Tuttavia, lo standard Unicode include altri caratteri spazio. Ne consegue che nel codice della libreria è stato eseguito un test per gli spazi vuoti errato.

1. Sostituire il confronto delle uguaglianze con una chiamata al metodo <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing riesegui automaticamente il metodo di test non riuscito.

   Live Unit Testing vengono visualizzati i risultati aggiornati, visualizzati anche nella finestra dell'editor di codice.

## <a name="see-also"></a>Vedi anche

- [Live Unit Testing con Visual Studio 2017](live-unit-testing.md)
- [Domande frequenti su Live Unit Testing](live-unit-testing-faq.yml)
