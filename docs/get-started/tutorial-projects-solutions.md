---
title: Introduzione a progetti e soluzioni
description: Informazioni sulla differenza tra progetti e soluzioni e su come usarli in Visual Studio.
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db3eea7017645d51065ed62e038c3323125e7b71
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431997"
---
# <a name="introduction-to-projects-and-solutions"></a>Introduzione a progetti e soluzioni

Questo articolo introduttivo illustra cosa significa  creare una soluzione e *un* progetto in Visual Studio. Una soluzione è un contenitore per organizzare uno o più progetti di codice correlati, ad esempio un progetto di libreria di classi e un progetto di test corrispondente.

Come esercizio didattico per comprendere il concetto di un progetto, si creerà una soluzione e un progetto da zero. In genere, si usano modelli di Visual Studio di *progetto* per creare nuovi progetti. Verranno anche esaminare le proprietà di un progetto e alcuni dei file che può contenere e creare un riferimento da un progetto a un altro.

> [!NOTE]
> Lo sviluppo di app Visual Studio non richiede soluzioni e progetti. È sufficiente aprire una cartella che contiene codice e iniziare a scrivere codice, compilare ed eseguire il debug. Ad esempio, un [GitHub](https://github.com/) clonato potrebbe non contenere Visual Studio e soluzioni. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).
::: moniker range="vs-2017"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se non è già stato installato Visual Studio 2019, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

::: moniker range=">=vs-2022"

Se non è già stato installato Visual Studio, passare alla pagina Visual Studio [download](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

## <a name="solutions-and-projects"></a>Soluzioni e progetti

In Visual Studio, una soluzione non è una "risposta". Una soluzione è semplicemente un contenitore Visual Studio per organizzare uno o più progetti correlati. Quando si apre una soluzione, Visual Studio carica automaticamente tutti i progetti contenuti nella soluzione.

### <a name="create-a-solution"></a>Creare una soluzione

Iniziare l'esplorazione creando una soluzione vuota. Dopo aver visto Visual Studio, è probabile che non si creino soluzioni vuote molto spesso. Quando si crea un nuovo progetto, Visual Studio crea automaticamente una soluzione per il progetto, a meno che non sia già aperta una soluzione.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Nella barra dei menu superiore selezionare **File** > **nuovo** > **Project**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

1. Nel riquadro sinistro espandere Altri Project **e** quindi **selezionare Visual Studio Soluzioni**. Nel riquadro centrale selezionare il **modello Soluzione** vuota. Assegnare alla soluzione **il nome QuickSolution** e quindi fare clic **sul pulsante OK.**

   ![Screenshot che mostra un modello di soluzione vuota selezionato in Visual Studio 2017.](media/tutorial-projects-new-solution.png "Modello di soluzione vuota in Visual Studio 2017.")

   La **Pagina iniziale** si chiude e viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

::: moniker range="vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale selezionare **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** immettere **una** soluzione vuota nella casella di ricerca, selezionare il **modello Soluzione** vuota e quindi **selezionare Avanti.**

   ![Screenshot che mostra un modello di soluzione vuota selezionato in Visual Studio 2019.](media/vs-2019/tutorial-projects-blank-solution-template.png "Modello di soluzione vuota in Visual Studio 2019.")

    > [!TIP]
    > Se sono installati diversi carichi di lavoro, il **modello Soluzione** vuota potrebbe non essere visualizzato nella parte superiore dell'elenco dei risultati della ricerca. Provare a scorrere fino alla **sezione Altri risultati in base alla sezione di** ricerca dell'elenco. Dovrebbe essere visualizzato qui.

4. Assegnare alla soluzione **il nome QuickSolution** e quindi selezionare **Crea**.

   Viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aprire Visual Studio e nella finestra iniziale selezionare **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** digitare *una* soluzione vuota nella casella di ricerca, selezionare il **modello Soluzione** vuota e quindi **selezionare Avanti.**

   :::image type="content" source="media/vs-2022/tutorial-projects-blank-solution-template.png" alt-text="Screenshot che mostra un modello di soluzione vuota selezionato in Visual Studio." border="false":::

    > [!TIP]
    > Se sono installati diversi carichi di lavoro, il **modello Soluzione** vuota potrebbe non essere visualizzato nella parte superiore dell'elenco dei risultati della ricerca. Provare a scorrere Altri **risultati in base alla ricerca per** trovare il modello.

4. Nella pagina **Configura il nuovo progetto** assegnare alla soluzione il nome **QuickSolution** e quindi selezionare **Crea**.

   La **soluzione QuickSolution** viene **visualizzata** Esplora soluzioni sul lato destro della Visual Studio finestra. Si userà spesso **Esplora soluzioni** per esplorare il contenuto dei progetti.

::: moniker-end

### <a name="add-a-project"></a>Aggiungere un progetto

Aggiungere ora il primo progetto alla soluzione. Iniziare con un progetto vuoto e aggiungere gli elementi necessari.

::: moniker range="vs-2017"

1. Nel menu di scelta rapida o nel menu di scelta rapida della soluzione **'QuickSolution'** **in** Esplora soluzioni selezionare **Aggiungi** > **nuovo Project**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual C#** e selezionare **Windows Desktop**. Nel riquadro centrale selezionare quindi il modello **Project vuoto (.NET Framework).** Assegnare al progetto **il nome QuickDate** e quindi **selezionare OK.**

   Il progetto QuickDate appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome *App.config*.

   > [!NOTE]
   > Se Visual **C#** non è visualizzato nel riquadro sinistro della finestra di dialogo, è necessario installare il carico di lavoro sviluppo **desktop .NET** Visual Studio. Visual Studio l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo. Un modo semplice per installare un nuovo carico di lavoro è selezionare il collegamento **Apri Programma di installazione di Visual Studio** nell'angolo inferiore sinistro della finestra di dialogo Aggiungi **nuovo Project** lavoro. Dopo Programma di installazione di Visual Studio, selezionare il carico di lavoro **Sviluppo desktop .NET** e quindi il **pulsante** Modifica.
   >
   > ![Screenshot che mostra il collegamento Programma di installazione di Visual Studio apri.](media/tutorial-projects-open-installer.png "Collegamento Apri Programma di installazione di Visual Studio nella finestra di dialogo Aggiungi nuovo Project in Visual Studio 2017.")

::: moniker-end

::: moniker range="vs-2019"

1. Nel menu di scelta rapida o nel menu di scelta rapida della soluzione **'QuickSolution'** **in** Esplora soluzioni selezionare **Aggiungi** > **nuovo Project**.

   Viene visualizzata la finestra di dialogo **Aggiungi un nuovo progetto**.

1. Immettere il testo **vuoto** nella casella di ricerca nella parte superiore e quindi selezionare **C#** in **Linguaggio**.

1. Selezionare il **modello Project (.NET Framework)** e quindi selezionare **Avanti.**

1. Assegnare al progetto **il nome QuickDate** e quindi **selezionare Crea**.

   Il progetto QuickDate appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome *App.config*.

   > [!NOTE]
   > Se il modello Empty **Project (.NET Framework)** non è visualizzato, è necessario installare il carico di lavoro **sviluppo desktop .NET** Visual Studio. Visual Studio l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo.
   >
   >Un modo semplice per installare un nuovo carico di lavoro  quando si crea un nuovo progetto è selezionare il collegamento Installa altri strumenti e funzionalità sotto il testo Non trovare quello che si **sta cercando?**. Dopo Programma di installazione di Visual Studio, selezionare il carico di lavoro **Sviluppo desktop .NET** e quindi il **pulsante** Modifica.
   >
   > ![Screenshot che mostra il collegamento Programma di installazione di Visual Studio apri.](media/vs-2019/tutorial-projects-open-installer.png "Collegamento Apri Programma di installazione di Visual Studio nella finestra di dialogo Crea un nuovo Project in Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. Fare clic con il pulsante destro del mouse  su Soluzione **"QuickSolution"** in **Esplora soluzioni** e scegliere > **Aggiungi nuovo Project** dal menu di scelta rapida.

1. Nella pagina **Aggiungi un nuovo progetto** digitare *vuoto* nella casella di ricerca nella parte superiore e selezionare **C#** in **Tutti i linguaggi**.

1. Selezionare il modello **C# Empty Project (.NET Framework)** e quindi selezionare **Avanti.**

   > [!NOTE]
   > Visual Studio l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo. Se il modello Empty **Project (.NET Framework)** non è visualizzato, è necessario installare il carico di lavoro **sviluppo desktop .NET** Visual Studio.
   >
   >Un modo semplice per installare un nuovo carico di lavoro  quando si crea un nuovo progetto è selezionare il collegamento Installa altri strumenti e funzionalità sotto il testo Non trovare quello che si **sta cercando?**. Nell'Programma di installazione di Visual Studio selezionare il carico di **lavoro Sviluppo di desktop .NET** e quindi selezionare **Modifica**.
   >
   > :::image type="content" source="media/vs-2022/tutorial-projects-open-installer.png" alt-text="Screenshot che mostra il collegamento Programma di installazione di Visual Studio apri." border="false":::

1. Nella pagina **Configura il nuovo progetto** assegnare al progetto il nome **QuickDate** e quindi selezionare **Crea**.

   Il **progetto QuickDate** viene visualizzato nella soluzione in **Esplora soluzioni**. Attualmente il progetto contiene un singolo file denominato **App.config**.

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Aggiungere un elemento al progetto

Aggiungere un file di codice al progetto vuoto.

1. Dal menu di scelta rapida o del menu di scelta rapida del **progetto QuickDate** **in** Esplora soluzioni selezionare **Aggiungi**  >  **nuovo elemento**.

   Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

1. Espandere **Elementi di Visual C#** e quindi selezionare **Codice**. Nel riquadro centrale selezionare il modello **di elemento** Classe. In **Nome** digitare *Calendario* e quindi selezionare **Aggiungi**.

   Visual Studio aggiunge un file denominato *Calendar.cs* al progetto. Il *file con estensione cs* alla fine è l'estensione di file di codice C#. Il file **Calendar.cs** viene visualizzato nella gerarchia **Esplora soluzioni** progetto visivo e il file viene aperto nell'editor.

1. Sostituire il contenuto del file *Calendar.cs* con il codice seguente:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Non è necessario comprendere ancora tutto ciò che il codice sta eseguendo. Eseguire l'app premendo **CTRL** F5 e verificare che l'app stampi la data odierna nella + finestra *della console* o dell'output standard.

## <a name="add-a-second-project"></a>Aggiungere un secondo progetto

Le soluzioni in genere contengono più di un progetto e questi progetti spesso fanno riferimento tra loro. Alcuni progetti in una soluzione potrebbero essere librerie di classi, altri potrebbero essere applicazioni eseguibili e altri potrebbero essere unit test progetti o siti Web.

Per aggiungere un unit test alla soluzione, iniziare da un modello di progetto in modo che non sia necessario aggiungere un altro file di codice al progetto.

::: moniker range="vs-2017"

1. Nel menu di scelta rapida o nel menu di scelta rapida della soluzione **'QuickSolution'** **in** Esplora soluzioni selezionare **Aggiungi** > **nuovo Project**.

2. Nel riquadro sinistro espandere **Visual C#** e selezionare la **categoria Test.** Nel riquadro centrale selezionare il modello di **progetto MSTest Test Project (.NET Core).** Assegnare al progetto **il nome QuickTest** e quindi selezionare **OK.**

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome *UnitTest1.cs*.

   ![Screenshot che mostra i Esplora soluzioni con due progetti.](media/tutorial-projects-solution-explorer.png "Esplora soluzioni con due progetti in Visual Studio 2017.")

::: moniker-end

::: moniker range="vs-2019"

1. Nel menu di scelta rapida o nel menu di scelta rapida della soluzione **'QuickSolution'** **in** Esplora soluzioni selezionare **Aggiungi** > **nuovo Project**.

2. Nella finestra di dialogo **Aggiungi un nuovo progetto** immettere il testo **unit test** nella casella di ricerca nella parte superiore e quindi selezionare **C#** in **Linguaggio**.

3. Selezionare il **modello di Project** unit test per .NET Core e quindi selezionare **Avanti.**

   > [!NOTE]
   > A partire da Visual Studio 2019 versione 16.9, il nome del modello di progetto MSTest è stato modificato da **MSTest Unit Test Project (.NET Core)** a **Unit Test Project**. Diversi passaggi nella creazione del progetto sono stati modificati in questo aggiornamento.

4. Assegnare al progetto **il nome QuickTest** e quindi selezionare **Avanti.**

5. Scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi **scegliere Crea**.

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome *UnitTest1.cs*.

   ![Screenshot che mostra i Esplora soluzioni con due progetti.](media/vs-2019/tutorial-projects-solution-explorer.png "Esplora soluzioni con due progetti in Visual Studio.")

::: moniker-end

::: moniker range=">=vs-2022"

1. Nel menu di scelta rapida o nel menu di scelta rapida della soluzione **'QuickSolution'** **in** Esplora soluzioni selezionare **Aggiungi** > **nuovo Project**.

1. Nella finestra **di dialogo** Aggiungi  un nuovo progetto digitare unit test nella casella di ricerca nella parte superiore e quindi selezionare **C#** in **Tutti i linguaggi**.

1. Selezionare il modello di progetto **C# Unit Test Project (.NET Framework)** e quindi selezionare **Avanti.**

1. Nella pagina **Configura il nuovo progetto** assegnare al progetto il nome *QuickTest* e quindi selezionare **Crea**.

   Visual Studio aggiunge il **progetto QuickTest** **a Esplora soluzioni** e il file **UnitTest1.cs** viene aperto nell'editor.

   :::image type="content" source="media/vs-2022/tutorial-projects-solution-explorer.png" alt-text="Screenshot che mostra i Esplora soluzioni con due progetti." border="false":::

::: moniker-end

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

Si userà il nuovo progetto unit test per testare il metodo nel progetto **QuickDate,** quindi è necessario aggiungere un riferimento a **QuickDate** al **progetto QuickTest.** L'aggiunta del riferimento *crea* una dipendenza di compilazione tra i due progetti, vale a dire che quando si compila la soluzione, **QuickDate** viene compilato prima **di QuickTest**.

::: moniker range="vs-2017"

1. Selezionare il **nodo Dipendenze** nel **progetto QuickTest** e scegliere Aggiungi riferimento dal menu di scelta rapida o dal menu di **scelta rapida.**

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **Progetti e** selezionare **Soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi selezionare **OK.**

   Viene aggiunto un riferimento al progetto **QuickDate**.

   ![Screenshot del Esplora soluzioni che mostra il riferimento al progetto in Visual Studio.](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Screenshot di un Esplora soluzioni che mostra un riferimento al progetto in Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. Selezionare il **nodo Dipendenze** nel progetto **QuickTest** e dal menu di scelta rapida o fare clic con il pulsante destro del mouse selezionare Aggiungi Project **riferimento**.

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **Progetti** e quindi selezionare **Soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi selezionare **OK.**

   Viene aggiunto un riferimento al progetto **QuickDate**.

   ![Screenshot del Esplora soluzioni che mostra un riferimento al progetto in Visual Studio 2019.](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo **Riferimenti** del **progetto QuickTest** e scegliere **Aggiungi** riferimento dal menu di scelta rapida.

1. Nella finestra **di dialogo Gestione** riferimenti in **Progetti** selezionare la casella di controllo accanto a **QuickDate** e quindi **selezionare OK.**

   Un riferimento al **progetto QuickDate** viene visualizzato nel **progetto QuickTest** in **Esplora soluzioni**.

   :::image type="content" source="media/vs-2022/tutorial-projects-solution-explorer-reference.png" alt-text="Screenshot di un Esplora soluzioni che mostra un riferimento al progetto." border="false":::

::: moniker-end

## <a name="add-test-code"></a>Aggiungere codice di test

1. Aggiungere ora il codice di test al file di codice di test C#. Sostituire il contenuto di *UnitTest1.cs* con il codice seguente:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Sotto parte del codice viene visualizzata una barra a linee rossa. È possibile correggere questo errore impostando il progetto di test come [assembly Friend](/dotnet/standard/assembly/friend-assemblies) nel **progetto QuickDate.**

1. Nel file *Calendar.cs* aggiungere l'istruzione [using](/dotnet/csharp/language-reference/keywords/using-statement) e l'attributo seguenti all'inizio del file per risolvere l'errore <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> nel progetto di test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Il **codice Calendar.cs** dovrebbe essere simile a questo screenshot:

   ::: moniker range="<=vs-2019"

   ![Screenshot che mostra il codice C Sharp.](media/tutorial-projects-cs-code.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/tutorial-projects-cs-code.png" alt-text="Screenshot che mostra il codice C Sharp." border="false":::

   ::: moniker-end

### <a name="run-the-unit-test"></a>Eseguire lo unit test

::: moniker range="vs-2017"

Se si vuole verificare che il unit test funzioni, scegliere **Test** Esegui tutti i test  >    >   dalla barra dei menu. Viene visualizzata la finestra **Esplora test**. Verificare che venga superato il testo **TestGetCurrentDate**.

::: moniker-end

::: moniker range=">=vs-2019"

Per verificare che il unit test funzioni, scegliere **Esegui test**  >  **tutti i** test dalla barra dei menu. Verrà **visualizzata la** finestra Esplora test e si dovrebbe verificare che il test **TestGetCurrentDate sia** stato superato.

::: moniker-end

::: moniker range="<=vs-2019"

![Screenshot che mostra Esplora test con un test superato.](media/tutorial-projects-test-explorer.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/tutorial-projects-test-explorer.png" alt-text="Screenshot che mostra Esplora test con un test superato." border="false":::

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Se **Esplora Test** non si apre automaticamente, aprirlo scegliendo **Test** > **Windows** > **Esplora Test** dalla barra dei menu.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Se **Esplora test** non si apre automaticamente, aprirlo scegliendo **Esplora**  >  **test** dalla barra dei menu.

::: moniker-end

## <a name="project-properties"></a>Proprietà progetto

La riga nel file *Calendar.cs* che contiene l'attributo fa riferimento al nome <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> dell'assembly o al nome file del progetto **QuickTest.** Il nome assembly può non corrispondere al nome del progetto. Per trovare il nome dell'assembly di un progetto, usare le proprietà del progetto. Le pagine proprietà contengono varie impostazioni per il progetto.

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul **progetto QuickTest** e scegliere Proprietà **oppure** selezionare il progetto e premere **ALT** + **INVIO.**

   Le *pagine delle* proprietà per il progetto vengono aperte nella **scheda** Applicazione. Il **nome dell'assembly** del progetto QuickTest è in effetti **QuickTest**.

   Se si vuole, è possibile modificare il nome qui. Quando si compila il progetto di test, il nome del file binario risultante cambia da *QuickTest.dll* a *\<NewName>.dll*.

    ::: moniker range="<=vs-2019"

    ![Screenshot che mostra le proprietà del progetto.](media/tutorial-projects-netcore-properties.png)

    ::: moniker-end

    ::: moniker range=">=vs-2022"

    :::image type="content" source="media/vs-2022/tutorial-project-properties.png" alt-text="Screenshot che mostra le proprietà del progetto." border="false":::

    ::: moniker-end

1. Esplorare le altre schede delle pagine delle proprietà del progetto, ad esempio **Compilazione** e **Debug**. Queste schede variano a seconda del tipo di progetto.

## <a name="see-also"></a>Vedi anche

- [Usare progetti e soluzioni](../ide/creating-solutions-and-projects.md)
- [Gestire le proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
