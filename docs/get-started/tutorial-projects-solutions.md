---
title: Introduzione a progetti e soluzioni
description: Informazioni sulla differenza tra progetti e soluzioni e su come usarli in Visual Studio.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cdc30b34c85a799827519af3cd2bba2c9f1735a
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668807"
---
# <a name="introduction-to-projects-and-solutions"></a>Introduzione a progetti e soluzioni

Questa articolo introduttivo spiega che cosa significa creare una *soluzione* e un *progetto* in Visual Studio. Una soluzione è un contenitore che consente di organizzare uno o più progetti di codice correlati, ad esempio, un progetto di libreria di classi e il progetto di test corrispondente. Si esaminano le proprietà di un progetto e alcuni dei file che può contenere. Verrà anche creato un riferimento da un progetto a un altro.

::: moniker range="vs-2017"

Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) per installarlo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se Visual Studio non è ancora installato, passare alla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads) per installarlo gratuitamente.

::: moniker-end

Una soluzione e un progetto verranno creati da zero, in un esercizio didattico che favorisce la comprensione del concetto di progetto. Nell'uso generico di Visual Studio è probabile che si usino alcuni dei numerosi *modelli* di progetto resi disponibili da Visual Studio per la creazione di un nuovo progetto.

> [!NOTE]
> Non è obbligatorio usare soluzioni e progetti per sviluppare app in Visual Studio. È anche possibile aprire semplicemente una cartella che contiene il codice e avviare la codifica, la compilazione e il debug. Se, ad esempio, si clona un repository [GitHub](https://github.com/) , è possibile che non contenga progetti e soluzioni di Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Soluzioni e progetti

Nonostante il nome, una soluzione non è una "risposta". Una soluzione è semplicemente un contenitore usato da Visual Studio per organizzare uno o più progetti correlati. Quando si apre una soluzione in Visual Studio, tutti i progetti contenuti al suo interno vengono caricati automaticamente.

### <a name="create-a-solution"></a>Creare una soluzione

Per iniziare si creerà una soluzione vuota. Una volta acquisita una conoscenza sufficiente di Visual Studio, la creazione di soluzioni vuote verrà probabilmente usata di rado. Quando si crea un nuovo progetto in Visual Studio, viene creata automaticamente una soluzione per ospitare il progetto, nel caso in cui non sia già presente una soluzione aperta.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Nella barra dei menu superiore selezionare **file** > **nuovo** > **progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

1. Nel riquadro sinistro espandere **altri tipi di progetto**, quindi selezionare **soluzioni di Visual Studio**. Nel riquadro centrale selezionare il modello di **soluzione vuota** . Assegnare alla soluzione il nome **QuickSolution**, quindi selezionare il pulsante **OK** .

   ![Modello di soluzione vuota in Visual Studio 2017](media/tutorial-projects-new-solution.png "Modello di soluzione vuota in Visual Studio 2017.")

   La **Pagina iniziale** si chiude e viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra Start selezionare **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** immettere **soluzione vuota** nella casella di ricerca, selezionare il modello **soluzione vuota** e quindi fare clic su **Avanti**.

   ![Modello Soluzione vuota in Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png "Modello di soluzione vuota in Visual Studio 2019.")

    > [!TIP]
    > Se sono installati più carichi di lavoro, il modello di **soluzione vuota** potrebbe non essere visualizzato nella parte superiore dell'elenco dei risultati della ricerca. Provare a scorrere gli **altri risultati in base** alla sezione di ricerca dell'elenco. Dovrebbe essere visualizzato qui.

4. Assegnare alla soluzione il nome **QuickSolution** e quindi selezionare **Crea**.

   Viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

### <a name="add-a-project"></a>Aggiungere un progetto

A questo punto si aggiunge il primo progetto alla soluzione. Si inizia con un progetto vuoto, quindi si aggiungono al progetto gli elementi necessari.

::: moniker range="vs-2017"

1. Dal menu di scelta rapida o dal menu di scelta rapida della **soluzione ' QuickSolution '** in **Esplora soluzioni** Selezionare **Aggiungi** > **nuovo progetto**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual C#** e selezionare desktop di **Windows**. Quindi, nel riquadro centrale, selezionare il modello di **progetto vuoto (.NET Framework)** . Assegnare al progetto il nome **QuickDate**, quindi fare clic su **OK**.

   Il progetto QuickDate appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome *App.config*.

   > [!NOTE]
   > Se **Visual C#** non è visibile nel riquadro sinistro della finestra di dialogo, è necessario installare il carico di lavoro di Visual Studio per **lo sviluppo di applicazioni desktop .NET** . Visual Studio usa l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo. Un modo semplice per installare un nuovo carico di lavoro consiste nel selezionare il collegamento **apri programma di installazione di Visual Studio** nell'angolo inferiore sinistro della finestra di dialogo **Aggiungi nuovo progetto** . Dopo l'avvio di Programma di installazione di Visual Studio, selezionare il carico di lavoro **sviluppo per desktop .NET** , quindi il pulsante **modifica** .
   >
   > ![Collegamento Apri il programma di installazione di Visual Studio](media/tutorial-projects-open-installer.png "Il collegamento Apri Programma di installazione di Visual Studio nella finestra di dialogo Aggiungi nuovo progetto in Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Dal menu di scelta rapida o dal menu di scelta rapida della **soluzione ' QuickSolution '** in **Esplora soluzioni** Selezionare **Aggiungi** > **nuovo progetto**.

   Viene visualizzata la finestra di dialogo **Aggiungi un nuovo progetto**.

1. Immettere il testo **vuoto** nella casella di ricerca nella parte superiore e quindi selezionare **C#** in **Linguaggio**.

1. Selezionare il modello **progetto vuoto (.NET Framework)** , quindi fare clic su **Avanti**.

1. Denominare il progetto **QuickDate**, quindi selezionare **Crea**.

   Il progetto QuickDate appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome *App.config*.

   > [!NOTE]
   > Se non viene visualizzato il modello di **progetto vuoto (.NET Framework)** , è necessario installare il carico di lavoro di Visual Studio per **lo sviluppo di applicazioni desktop .NET** . Visual Studio usa l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo.
   >
   >Un modo semplice per installare un nuovo carico di lavoro quando si crea un nuovo progetto consiste nel selezionare il collegamento **Installa altri strumenti e funzionalità** nel testo che indica che **non è stato trovato ciò che si sta cercando**. Dopo l'avvio di Programma di installazione di Visual Studio, selezionare il carico di lavoro **sviluppo per desktop .NET** , quindi il pulsante **modifica** .
   >
   > ![Collegamento Apri il programma di installazione di Visual Studio](media/vs-2019/tutorial-projects-open-installer.png "Il collegamento Apri Programma di installazione di Visual Studio nella finestra di dialogo Crea un nuovo progetto in Visual Studio.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Aggiungere un elemento al progetto

Ora il progetto è vuoto. Aggiungiamo un file di codice.

1. Scegliere **Aggiungi** nuovo elemento dal menu di scelta rapida del progetto **QuickDate** in **Esplora soluzioni**  >  .

   Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

1. Espandere **elementi di Visual C#**, quindi selezionare **codice**. Nel riquadro centrale selezionare il modello di elemento **classe** . Assegnare un nome al **Calendario** della classe e quindi selezionare il pulsante **Aggiungi** .

   Un file denominato *Calendar.cs* viene aggiunto al progetto. Il valore *cs* finale è l'estensione del nome file assegnata ai file di codice C#. Il file appare nella gerarchia visuale del progetto in **Esplora soluzioni** e il suo contenuto viene aperto nell'editor.

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

   Non è necessario comprendere il funzionamento del codice, ma se lo si desidera, è possibile eseguire il programma premendo **CTRL** + **F5** e verificare che la data odierna venga stampata nella finestra della console (o output standard).

## <a name="add-a-second-project"></a>Aggiungere un secondo progetto

Molto spesso le soluzioni contengono più di un progetto e spesso tali progetti includono riferimenti reciproci. Alcuni progetti di una soluzione possono essere librerie di classi, altri possono essere applicazioni eseguibili e altri ancora progetti unit test o siti Web.

Ora si aggiungerà un progetto unit test alla soluzione. Questa volta si inizierà con un modello di progetto, pertanto non sarà necessario inserire un file di codice aggiuntivo nel progetto.

1. Dal menu di scelta rapida o dal menu di scelta rapida della **soluzione ' QuickSolution '** in **Esplora soluzioni** Selezionare **Aggiungi**  >  **nuovo progetto**.

::: moniker range="vs-2017"

2. Nel riquadro sinistro espandere **Visual C#** e selezionare la categoria **test** . Nel riquadro centrale selezionare il modello di progetto del **progetto di test MSTest (.NET Core)** . Assegnare al progetto il nome **QuickTest** e quindi fare clic su **OK**.

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome *UnitTest1.cs*.

   ![Esplora soluzioni di Visual Studio con due progetti](media/tutorial-projects-solution-explorer.png "Esplora soluzioni con due progetti in Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

2. Nella finestra di dialogo **Aggiungi un nuovo progetto** immettere il testo **unit test** nella casella di ricerca nella parte superiore e quindi selezionare **C#** in **Linguaggio**.

3. Selezionare il modello di progetto di **test MSTest (.NET Core)** e quindi fare clic su **Avanti**.

4. Assegnare al progetto il nome **QuickTest** e quindi selezionare **Crea**.

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome *UnitTest1.cs*.

   ![Esplora soluzioni di Visual Studio con due progetti](media/vs-2019/tutorial-projects-solution-explorer.png "Esplora soluzioni con due progetti in Visual Studio.")

::: moniker-end

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

Il nuovo progetto unit test verrà utilizzato per il test del metodo nel progetto **QuickDate**, pertanto è necessario aggiungere un riferimento a tale progetto. Questa operazione crea una *dipendenza di compilazione*, vale a dire che quando si crea la soluzione, **QuickDate** viene compilato prima di **QuickTest**.

::: moniker range="vs-2017"

1. Selezionare il nodo **dipendenze** nel progetto **QuickTest** e dal menu di scelta rapida fare clic su **Aggiungi riferimento**.

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **progetti** e selezionare **soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi fare clic su **OK**.

   Viene aggiunto un riferimento al progetto **QuickDate**.

   ![Screenshot del Esplora soluzioni che mostra il riferimento al progetto in Visual Studio](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Screenshot di Esplora soluzioni che mostra un riferimento a un progetto in Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. Selezionare il nodo **dipendenze** nel progetto **QuickTest** e scegliere **Aggiungi riferimento al progetto** dal menu di scelta rapida.

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **progetti**, quindi selezionare **soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi fare clic su **OK**.

   Viene aggiunto un riferimento al progetto **QuickDate**.

   ![Screenshot di Esplora soluzioni che mostra un riferimento a un progetto in Visual Studio 2019](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

## <a name="add-test-code"></a>Aggiungere codice di test

1. Ora si aggiungerà codice di test al file di codice di test C#. Sostituire il contenuto di *UnitTest1.cs* con il codice seguente:

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

   Sotto alcune parti del codice viene visualizzata una linea rossa ondulata. Per risolvere l'errore si imposterà il progetto di test come [assembly Friend](/dotnet/standard/assembly/friend-assemblies) del progetto **QuickDate**.

1. Nel progetto **QuickDate** aprire il file *Calendar.cs* se non è già aperto. Aggiungere l'[istruzione using](/dotnet/csharp/language-reference/keywords/using-statement) e l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> seguenti nella parte superiore del file per risolvere l'errore nel progetto di test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Il file di codice sarà simile al seguente:

   ![Codice CSharp](media/tutorial-projects-cs-code.png "Frammento di codice della sezione Aggiungi codice di test in questo articolo.")

## <a name="project-properties"></a>Proprietà progetto

La riga del file *Calendar.cs* contenente l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> fa riferimento al nome assembly, cioè al nome file, del progetto **QuickTest**. Il nome assembly può non corrispondere al nome del progetto. Per trovare il nome assembly di un progetto, aprire le proprietà del progetto.

1. In **Esplora soluzioni** selezionare il progetto **QuickTest**. Nel menu di scelta rapida o nel menu a comparsa selezionare **Proprietà** oppure premere semplicemente **ALT**+**INVIO**.

   Le *pagine delle proprietà* per il progetto vengono aperte nella scheda **applicazione** . Le pagine delle proprietà contengono diverse impostazioni per il progetto. Si noti che il nome assembly del progetto **QuickTest** è di fatto "QuickTest". Se si desidera modificarlo, farlo qui. Se lo si modifica, quando si compila il progetto di test, il nome del file binario cambia da *QuickTest.dll* al nome scelto.

   ![Proprietà progetto](media/tutorial-projects-netcore-properties.png "Finestra di dialogo delle proprietà del progetto in Visual Studio.")

1. Esplorare le altre schede delle pagine delle proprietà del progetto, ad esempio **Compilazione** e **Debug**. Queste schede variano a seconda del tipo di progetto.

## <a name="next-steps"></a>Passaggi successivi

Per verificare che il unit test funzioni, selezionare **test**  >  **Esegui**  >  **tutti i test** dalla barra dei menu. Viene visualizzata la finestra **Esplora test**. Verificare che venga superato il testo **TestGetCurrentDate**.

![Esplora test in Visual Studio mostra che il test è stato superato](media/tutorial-projects-test-explorer.png "Esplora test in Visual Studio che mostra un test superato.")

::: moniker range="vs-2017"

> [!TIP]
> Se **Esplora Test** non si apre automaticamente, aprirlo scegliendo **Test** > **Windows** > **Esplora Test** dalla barra dei menu.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Se **Esplora test** non viene aperto automaticamente, aprirlo **scegliendo**  >  **Esplora test** test dalla barra dei menu.

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Usare progetti e soluzioni](../ide/creating-solutions-and-projects.md)
- [Gestire le proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Panoramica dell'ambiente IDE di Visual Studio](../get-started/visual-studio-ide.md)
