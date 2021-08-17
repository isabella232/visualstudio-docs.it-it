---
title: "Procedura dettagliata: Creare un'applicazione"
description: Acquisire familiarità con diverse opzioni che è possibile configurare quando si compilano applicazioni con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/25/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a1e3ffeab11b8e1fd88800e854febe10d93da6ce6c30ce55512fddb3efaff0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371495"
---
# <a name="walkthrough-build-an-application"></a>Procedura dettagliata: Creare un'applicazione

Completando questa procedura dettagliata è possibile acquisire familiarità con numerose opzioni che possono essere configurate quando si compilano applicazioni con Visual Studio. Verrà illustrato come creare una configurazione della build personalizzata, nascondere alcuni messaggi di avviso e aumentare le informazioni di output di compilazione per un'applicazione di esempio.

## <a name="install-the-sample-application"></a>Installare l'applicazione di esempio

Scaricare l'esempio [Introduzione alla creazione di applicazioni WPF](https://code.msdn.microsoft.com/Introduction-to-Building-b8d16419). Scegliere C# o Visual Basic. Dopo aver scaricato il file con estensione *zip*, estrarlo e aprire il file *ExpenseItIntro.sln* usando Visual Studio.

## <a name="create-a-custom-build-configuration"></a>Creare una configurazione della build personalizzata

Quando si crea una soluzione, le configurazioni della build di versione e di debug e le relative destinazioni della piattaforma predefinite sono definite automaticamente per la soluzione. È quindi possibile personalizzare queste configurazioni o crearne di proprie. Le configurazioni della build specificano il tipo di compilazione. Le piattaforme di compilazione specificano il sistema operativo a cui è rivolta un'applicazione per la configurazione. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md), [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md) e [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).

È possibile modificare o creare configurazioni e impostazioni piattaforma usando la finestra di dialogo **Gestione configurazione**. In questa procedura si creerà una configurazione della build per il test.

### <a name="create-a-build-configuration"></a>Creare una configurazione della build

1. Aprire la finestra di dialogo **Gestione configurazione**.

   ![Menu Compila, comando Gestione configurazione](../ide/media/buildwalk_configurationmanagerdialogbox.png)

1. **Nell'elenco Configurazione soluzione** attiva scegliere **\<New...\>** .

1. Nella finestra di dialogo **Nuova configurazione soluzione** assegnare il nome `Test` alla nuova configurazione, copiare le impostazioni dalla configurazione **Debug** esistente e quindi scegliere **OK**.

   ![Finestra di dialogo Nuova configurazione soluzione](../ide/media/buildwalk_newsolutionconfigdlgbox.png)

1. **Nell'elenco Piattaforma soluzione** attiva scegliere **\<New...\>** .

1. Nella finestra **di dialogo** Nuova piattaforma soluzione scegliere **x64** e non copiare le impostazioni dalla piattaforma x86.

   ![Finestra di dialogo Nuova piattaforma soluzione](../ide/media/buildwalk_newsolutionplatform.png)

1. Fare clic su **OK** .

   La configurazione della soluzione attiva è stata modificata in **Test** con la piattaforma della soluzione attiva impostata su x64.

   ![Gestione configurazione con Configurazione di test](../ide/media/buildwalk_configmanagertestconfig.png)

1. Scegliere **Chiudi**.

È possibile verificare o modificare rapidamente la configurazione della soluzione attiva tramite l'elenco **Configurazioni soluzione** nella barra degli strumenti **Standard**.

![Opzione Configurazione soluzione, barra degli strumenti standard](../ide/media/buildwalk_standardtoolbarsolutioncongfig.png)

## <a name="build-the-application"></a>Compilare l'applicazione

Successivamente verrà creata la soluzione con la configurazione della build personalizzata.

### <a name="build-the-solution"></a>Compilare la soluzione

- Sulla barra dei menu scegliere **Compila**  >  **soluzione o** premere **CTRL** + **MAIUSC** + **B.**

    Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata.

## <a name="hide-compiler-warnings"></a>Nascondere gli avvisi del compilatore

A questo punto viene presentata la parte del codice che determina un avviso generato dal compilatore.

1. Nel progetto C# aprire il file *ExpenseReportPage.xaml.cs*. Nel metodo **ExpenseReportPage** aggiungere il codice seguente: `int i;`.

    OR

    Nel progetto Visual Basic aprire il file *ExpenseReportPage.xaml.vb*. Nel costruttore personalizzato **Public Sub New...** aggiungere il codice seguente: `Dim i`.

1. Compilare la soluzione.

Nella finestra **Output** vengono visualizzati i risultati della compilazione. La compilazione è stata completata, ma sono stati generati avvisi:

![Finestra di output Visual Basic](../ide/media/buildwalk_vbbuildoutputwnd.png)

![Finestra di output Visual C&#35;](../ide/media/buildwalk_csharpbuildoutputwnd.png)

È possibile nascondere temporaneamente determinati messaggi di avviso durante una compilazione anziché lasciare che ingombrino l'output di compilazione.

### <a name="hide-a-specific-c-warning"></a>Nascondere un avviso specifico di C#

1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.

1. Sulla barra dei menu scegliere **Visualizza pagine**  >  **delle proprietà.**

     Si apre la finestra **Creazione progetti**.

1. Scegliere la pagina **Compilazione** e specificare il numero di avviso **0168** nella casella **Non visualizzare avvisi**.

     ![Pagina Compilazione, Progettazione progetti](../ide/media/buildwalk_csharpsuppresswarnings.png)

     Per altre informazioni, vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).

1. Compilare la soluzione.

     Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.

     ![Finestra di output, avvisi di compilazione di Visual C&#35;](../ide/media/buildwalk_visualcsharpbuildwarnings.png)

### <a name="suppress-all-visual-basic-build-warnings"></a>Eliminare tutti gli avvisi di compilazione di Visual Basic

1. Scegliere il nodo di progetto di primo livello in **Esplora soluzioni**.

2. Sulla barra dei menu scegliere **Visualizza pagine**  >  **delle proprietà.**

     Si apre la finestra **Creazione progetti**.

3. Nella pagina **Compilazione** selezionare la casella di controllo **Disabilita tutti gli avvisi**.

     ![Pagina Compila, Progettazione progetti](../ide/media/buildwalk_vbsuppresswarnings.png)

     Per altre informazioni, vedere [Configurare gli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

4. Compilare la soluzione.

   Nella finestra **Output** vengono visualizzate solo le informazioni di riepilogo per la compilazione.

   ![Finestra di output, avvisi di compilazione di Visual Basic](../ide/media/buildwalk_visualbasicbuildwarnings.png)

   Per altre informazioni, vedere [Procedura: Non visualizzare avvisi del compilatore](../ide/how-to-suppress-compiler-warnings.md).

## <a name="display-additional-build-details-in-the-output-window"></a>Visualizzare dettagli di compilazione aggiuntivi nella finestra di output

È possibile modificare la quantità di informazioni sul processo di compilazione visualizzate nella finestra **Output**. Il livello di dettaglio di compilazione è in genere impostato su **Minimo**. Ciò significa che nella finestra **Output** viene visualizzato solo un riepilogo del processo di compilazione insieme a eventuali errori o avvisi di priorità alta. È possibile visualizzare altre informazioni sulla compilazione tramite la [finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md).

> [!IMPORTANT]
> Se si visualizzano maggiori informazioni, il completamento della compilazione richiederà più tempo.

### <a name="change-the-amount-of-information-in-the-output-window"></a>Modificare la quantità di informazioni nella finestra Output

1. Aprire la finestra di dialogo **Opzioni**.

     ![Comando Opzioni nel menu Strumenti](../ide/media/exploreide-toolsoptionsmenu.png)

1. Scegliere la categoria **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.

1. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi **OK**.

1. Nella barra dei menu scegliere **Compila**  >  **soluzione pulita.**

1. Compilare la soluzione e quindi esaminare le informazioni nella finestra **Output**.

     Le informazioni sulla compilazione includono l'ora di inizio della compilazione (indicata all'inizio) e l'ordine in cui i file sono stati elaborati. Queste informazioni includono anche la sintassi del compilatore effettiva che Visual Studio esegue durante la compilazione.

     Nella compilazione C#, ad esempio, l'opzione [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) elenca il codice di avviso **0168** specificato in precedenza in questo argomento, insieme ad altri tre avvisi.

     Nella compilazione Visual Basic, [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) non include avvisi specifici da escludere, quindi non viene visualizzato alcun avviso.

    > [!TIP]
    > È possibile cercare il contenuto della finestra **Output** se si visualizza la finestra di dialogo **Trova** scegliendo i tasti **CTRL**+**F**.

Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).

## <a name="create-a-release-build"></a>Creare una build di versione

È possibile compilare una versione dell'applicazione di esempio ottimizzata per la spedizione. Per la build di versione, si specificherà che il file eseguibile venga copiato in una condivisione di rete prima dell'avvio della compilazione.

Per altre informazioni, vedere [Procedura: Modificare la directory dell'output compilato](../ide/how-to-change-the-build-output-directory.md) e [Compilare e pulire progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md).

### <a name="specify-a-release-build-for-visual-basic"></a>Specificare una build di versione per Visual Basic

1. Aprire **Creazione progetti**.

     ![Menu Visualizza, comando Pagine delle proprietà](../ide/media/buildwalk_viewpropertypages.png)

1. Scegliere la pagina **Compilazione**.

1. Nell'elenco **Configurazione** scegliere **Versione**.

1. Nell'elenco **Piattaforma** scegliere **x86**.

1. Specificare un percorso di compilazione nella casella **Percorso dell'output di compilazione**.

     Ad esempio, è possibile specificare `\\myserver\builds`.

    > [!IMPORTANT]
    > Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere **il pulsante OK** nella finestra di messaggio.

1. Compilare l'applicazione.

     ![Comando Compila soluzione del menu Compila](../ide/media/exploreide-buildsolution.png)

### <a name="specify-a-release-build-for-c"></a>Specificare una build di versione per Visual C\#

1. Aprire **Creazione progetti**.

     ![Menu Visualizza, comando Pagine delle proprietà](../ide/media/buildwalk_viewpropertypages.png)

1. Scegliere la scheda **Compila**.

1. Nell'elenco **Configurazione** scegliere **Versione**.

1. Nell'elenco **Piattaforma** scegliere **x86**.

1. Specificare un percorso di rete nella casella **Percorso output**.

     Ad esempio è possibile specificare `\\myserver\builds`.

    > [!IMPORTANT]
    > Potrebbe essere visualizzata una finestra di messaggio che informa che la condivisione di rete specificata potrebbe non essere una posizione attendibile. Se si considera attendibile il percorso specificato, scegliere **il pulsante OK** nella finestra di messaggio.

1. Nella **barra degli strumenti Standard** impostare le opzioni Configurazioni soluzione su **Release** e Piattaforme soluzione su **x86**.

1. Compilare l'applicazione.

     ![Comando Compila soluzione del menu Compila](../ide/media/exploreide-buildsolution.png)

   Il file eseguibile viene copiato nel percorso di rete specificato. Il percorso corrispondente sarà `\\myserver\builds\\FileName.exe`.

Congratulazioni! Questa procedura dettagliata è stata completata correttamente.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Compilare un progetto (C++)](/cpp/ide/walkthrough-building-a-project-cpp)
- [Panoramica della precompilazione del progetto di applicazione Web ASP.NET](/previous-versions/aspnet/aa983464\(v\=vs.110\))
- [Procedura dettagliata: Usare MSBuild](../msbuild/walkthrough-using-msbuild.md)
