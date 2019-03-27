---
title: Introduzione a progetti e soluzioni
ms.date: 12/11/2017
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a87080f2c6bc92bc37cc98a08bfc6643e3d12c4
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324133"
---
# <a name="learn-about-projects-and-solutions"></a>Informazioni su progetti e soluzioni

Questa articolo introduttivo spiega che cosa significa creare una *soluzione* e un *progetto* in Visual Studio. Una soluzione è un contenitore che consente di organizzare uno o più progetti di codice correlati, ad esempio, un progetto di libreria di classi e il progetto di test corrispondente. Si esaminano le proprietà di un progetto e alcuni dei file che può contenere. Verrà anche creato un riferimento da un progetto a un altro.

Se Visual Studio non è ancora installato, accedere alla pagina [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) per installarlo gratuitamente.

Una soluzione e un progetto verranno creati da zero, in un esercizio didattico che favorisce la comprensione del concetto di progetto. Nell'uso generico di Visual Studio è probabile che si usino alcuni dei numerosi *modelli* di progetto resi disponibili da Visual Studio per la creazione di un nuovo progetto.

> [!NOTE]
> Non è obbligatorio usare soluzioni e progetti per sviluppare app in Visual Studio. È anche possibile aprire semplicemente una cartella che contiene il codice e avviare la codifica, la compilazione e il debug. Se, ad esempio, si clona un repository di [GitHub](https://github.com/), è possibile che questo non contenga soluzioni e progetti di Visual Studio. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Soluzioni e progetti

Nonostante il nome, una soluzione non è una "risposta". Una soluzione è semplicemente un contenitore usato da Visual Studio per organizzare uno o più progetti correlati. Quando si apre una soluzione in Visual Studio, tutti i progetti contenuti al suo interno vengono caricati automaticamente.

### <a name="create-a-solution"></a>Creare una soluzione

Per iniziare si creerà una soluzione vuota. Una volta acquisita una conoscenza sufficiente di Visual Studio, la creazione di soluzioni vuote verrà probabilmente usata di rado. Quando si crea un nuovo progetto in Visual Studio, viene creata automaticamente una soluzione per ospitare il progetto, nel caso in cui non sia già presente una soluzione aperta.

::: moniker range="vs-2017"

1. Aprire Visual Studio.

1. Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

1. Nel riquadro sinistro espandere **Altri tipi di progetti**, quindi scegliere **Soluzioni di Visual Studio**. Nel riquadro centrale scegliere il modello **Soluzione vuota**. Assegnare alla soluzione il nome **QuickSolution**, quindi scegliere il pulsante **OK**.

   ![Modello Soluzione vuota in Visual Studio](media/tutorial-projects-new-solution.png)

   La **Pagina iniziale** si chiude e viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire Visual Studio.

2. Nella finestra iniziale scegliere **Crea un nuovo progetto**.

3. Nella pagina **Crea un nuovo progetto** immettere **soluzione vuota** nella casella di ricerca, selezionare il modello **Soluzione vuota** e quindi scegliere **Avanti**.

4. Assegnare alla soluzione il nome **QuickSolution**, quindi scegliere **Crea**.

   Viene visualizzata una soluzione in **Esplora soluzioni** sul lato destro della finestra di Visual Studio. **Esplora soluzioni** viene usato di frequente, per visualizzare il contenuto dei progetti.

::: moniker-end

### <a name="add-a-project"></a>Aggiungere un progetto

A questo punto si aggiunge il primo progetto alla soluzione. Si inizia con un progetto vuoto, quindi si aggiungono al progetto gli elementi necessari.

1. Nel menu di scelta rapida o nel menu a comparsa **Soluzione 'QuickSolution'** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo progetto**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual C#** e scegliere **Desktop di Windows**. Nel riquadro centrale scegliere il modello **Progetto vuoto (.NET Framework)**. Assegnare al progetto il nome **QuickDate** e scegliere **OK**.

   Il progetto QuickDate appare sotto la soluzione in **Esplora soluzioni**. Attualmente contiene un unico file con nome *App.config*.

   > [!NOTE]
   > Se **Visual C#** non viene visualizzato nel riquadro sinistro della finestra di dialogo, è necessario installare il **carico di lavoro** *Sviluppo per desktop .NET* di Visual Studio. Visual Studio usa l'installazione basata sul carico di lavoro per installare solo i componenti necessari per il tipo di sviluppo scelto. Un modo facile per installare un nuovo carico di lavoro consiste nello scegliere il collegamento **Apri il programma di installazione di Visual Studio** nell'angolo in basso a sinistra della finestra di dialogo **Aggiungi nuovo progetto**. Dopo l'avvio del programma di installazione di Visual Studio, scegliere il carico di lavoro **Sviluppo per desktop .NET** e quindi il pulsante **Modifica**.

   ![Collegamento Apri il programma di installazione di Visual Studio](media/tutorial-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Aggiungere un elemento al progetto

Ora il progetto è vuoto. Aggiungiamo un file di codice.

1. Nel menu di scelta rapida o nel menu a comparsa del progetto **QuickDate** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo elemento**.

   Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.

1. Espandere **Elementi di Visual C#**, quindi scegliere **Codice**. Nel riquadro centrale scegliere il modello dell'elemento **Classe**. Assegnare il nome **Calendar** alla classe e scegliere il pulsante **Aggiungi**.

   Il file *Calendar.cs* viene aggiunto al progetto. Il valore *cs* finale è l'estensione del nome file assegnata ai file di codice C#. Il file appare nella gerarchia visuale del progetto in **Esplora soluzioni** e il suo contenuto viene aperto nell'editor.

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

   In questa fase non è necessario comprendere le operazioni eseguite dal codice. Se si vuole, è possibile eseguire il programma premendo **Ctrl**+**F5** e verificare che visualizza la data corrente nella finestra della console o di output standard.

## <a name="add-a-second-project"></a>Aggiungere un secondo progetto

Molto spesso le soluzioni contengono più di un progetto e spesso tali progetti includono riferimenti reciproci. Alcuni progetti di una soluzione possono essere librerie di classi, altri possono essere applicazioni eseguibili e altri ancora progetti unit test o siti Web.

Ora si aggiungerà un progetto unit test alla soluzione. Questa volta si inizierà con un modello di progetto, pertanto non sarà necessario inserire un file di codice aggiuntivo nel progetto.

1. Nel menu di scelta rapida o nel menu a comparsa **Soluzione 'QuickSolution'** in **Esplora soluzioni** scegliere **Aggiungi** > **Nuovo progetto**.

   Verrà aperta la finestra di dialogo **Aggiungi nuovo progetto** .

1. Nel riquadro sinistro espandere **Visual Basic** e scegliere la categoria **Test**. Nel riquadro centrale scegliere il modello di progetto **Progetto unit test (.NET Framework)**. Assegnare al progetto il nome **QuickTest** e scegliere il pulsante **OK**.

   Viene aggiunto un secondo progetto a **Esplora soluzioni** e nell'editor viene aperto un file con nome *UnitTest1.vb*. *vb* è l'estensione di nome file assegnata ai file di codice di Visual Basic.

   ![Esplora soluzioni di Visual Studio con due progetti](media/tutorial-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Aggiungere un riferimento al progetto

Il nuovo progetto unit test verrà utilizzato per il test del metodo nel progetto **QuickDate**, pertanto è necessario aggiungere un riferimento a tale progetto. Questa operazione crea una *dipendenza di compilazione*, vale a dire che quando si crea la soluzione, **QuickDate** viene compilato prima di **QuickTest**.

1. Scegliere il nodo **Riferimenti** nel progetto **QuickTest**, quindi nel menu di scelta rapida o nel menu a comparsa scegliere **Aggiungi riferimento**.

   ![Menu Aggiungi riferimento](media/tutorial-projects-add-reference.png)

   Viene visualizzata la finestra di dialogo **Gestione riferimenti**.

1. Nel riquadro sinistro espandere **Progetti** e scegliere **Soluzione**. Nel riquadro centrale selezionare la casella di controllo accanto a **QuickDate** e quindi scegliere il pulsante **OK**.

   Viene aggiunto un riferimento al progetto **QuickDate**.

## <a name="add-test-code"></a>Aggiungere codice di test

1. Ora si aggiungerà codice di test al file di codice di Visual Basic. Sostituire il contenuto di *UnitTest1.vb* con il codice seguente.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Sotto alcune parti del codice viene visualizzata una linea rossa ondulata. Per risolvere l'errore si imposterà il progetto di test come [assembly Friend](/dotnet/standard/assembly/friend-assemblies) del progetto **QuickDate**.

1. Tornare al progetto **QuickDate**, aprire il file *Calendar.cs*, se non è già aperto, e aggiungere la seguente [istruzione using](/dotnet/csharp/language-reference/keywords/using-statement) e l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> all'inizio del file per risolvere l'errore nel progetto di test.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Il file di codice sarà simile al seguente:

   ![Codice CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Proprietà di progetti

La riga del file *Calendar.cs* contenente l'attributo <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> fa riferimento al nome assembly, cioè al nome file, del progetto **QuickTest**. Il nome assembly può non corrispondere al nome del progetto. Per trovare il nome assembly di un progetto, aprire le proprietà del progetto.

1. In **Esplora soluzioni** selezionare il progetto **QuickTest**. Nel menu di scelta rapida o nel menu a comparsa selezionare **Proprietà** oppure premere semplicemente **ALT**+**INVIO**.

   Le *pagine proprietà* del progetto vengono aperte nella scheda **Applicazione**. Le pagine proprietà contengono varie impostazioni per il progetto. Si noti che il nome assembly del progetto **QuickTest** è di fatto "QuickTest". Se si desidera modificarlo, farlo qui. Se lo si modifica, quando si compila il progetto di test, il nome del file binario cambia da *QuickTest.dll* al nome scelto.

   ![Proprietà di progetti](media/tutorial-projects-properties.png)

1. Esplorare le altre schede delle pagine proprietà del progetto, quali **Compilazione** e **Impostazioni**. Queste schede variano a seconda del tipo di progetto.

## <a name="next-steps"></a>Passaggi successivi

Per verificare che l'unit test funzioni scegliere **Test** > **Esegui** > **Tutti i test** nella barra dei menu. Viene visualizzata la finestra **Esplora test**. Verificare che venga superato il testo **TestGetCurrentDate**.

![Esplora test in Visual Studio mostra che il test è stato superato](media/tutorial-projects-test-explorer.png)

> [!TIP]
> Se **Esplora Test** non si apre automaticamente, aprirlo scegliendo **Test** > **Windows** > **Esplora Test** dalla barra dei menu.

## <a name="see-also"></a>Vedere anche

- [Creare soluzioni e progetti](../ide/creating-solutions-and-projects.md)
- [Gestione delle proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)
- [Gestire i riferimenti in un progetto](../ide/managing-references-in-a-project.md)
- [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)
