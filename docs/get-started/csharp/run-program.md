---
title: Come eseguire un programma (C#)
description: Guida per principianti su come eseguire un programma C# in Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f68039ca8b1bca3224766f7f2673514e3b6a2e9f
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428029"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Procedura: Eseguire un programma C# in Visual Studio

La modalità di esecuzione di un programma dipende dall'origine, dal tipo di programma e dall'eventuale esecuzione nel debugger. Nel caso più semplice, per compilare ed eseguire un progetto aperto in Visual Studio:

- Premere **F5,** scegliere **Avvia** debug con debug dal menu Visual Studio oppure selezionare la freccia Start verde e il nome del progetto sulla barra  >   Visual Studio  comandi.
- In caso contrario, per eseguire senza eseguire il debug, premere **CTRL** F5 o scegliere Avvia debug senza eseguire +    >  **debug** dal menu Visual Studio debug.

::: moniker range="<=vs-2019"
![Screenshot che mostra il pulsante Start.](media/vs-start-button.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/start-button.png" alt-text="Screenshot che mostra il pulsante Start." border="false":::
::: moniker-end

## <a name="start-from-a-project"></a>Iniziare da un progetto

È possibile eseguire un progetto C# o un file *con estensione csproj* se si tratta di un programma runnable. Se il progetto contiene un file C# con un metodo e il relativo output è un file eseguibile o.exe, probabilmente verrà eseguito se viene `Main` compilato correttamente. 

1. Se il codice del programma è già in un progetto Visual Studio, aprire il progetto. A tale scopo, è possibile fare doppio clic o toccare il file con estensione csproj in Windows Esplora file oppure scegliere Apri un progetto **in** Visual Studio, individuare il file con estensione *csproj* e selezionare il file. 

1. Dopo il caricamento del progetto Visual Studio, se la soluzione Visual Studio ha più di un progetto, assicurarsi di impostare il progetto con il metodo come `Main` progetto di avvio. Per impostare il progetto di avvio, fare clic con il pulsante destro del mouse sul nome del progetto o sul nodo in **Esplora soluzioni** e scegliere Imposta come Project **dal** menu di scelta rapida.

   ::: moniker range="<=vs-2019"
   ![Screenshot che mostra l'impostazione del progetto di avvio.](media/set-as-startup-project.png)
   ::: moniker-end
   ::: moniker range=">=vs-2022"
   :::image type="content" source="media/vs-2022/set-startup-project.png" alt-text="Screenshot che mostra l'impostazione del progetto di avvio." border="false":::
   ::: moniker-end

1. Per eseguire il programma, premere **CTRL** + **F5,** selezionare **Avvia** debug senza eseguire debug dal menu superiore o  >   selezionare il pulsante **Start** verde. 

   Visual Studio tenta di compilare ed eseguire il progetto. Nella parte inferiore della schermata Visual Studio, l'output di compilazione viene visualizzato nella finestra **Output** e gli eventuali errori di compilazione vengono visualizzati nella **finestra Elenco** errori.

   Se la compilazione ha esito positivo, l'app viene eseguita nel modo appropriato per il tipo di progetto. Le app console vengono eseguite in una finestra del terminale, Windows le app desktop vengono avviate in una nuova finestra desktop e le app Web vengono eseguite in un browser ospitato da IIS Express.

## <a name="start-from-code"></a>Iniziare dal codice

Se si inizia da un elenco di codice, da un file di codice o da un numero ridotto di file, assicurarsi innanzitutto che il codice sia un programma eseguibile da un'origine attendibile. Qualsiasi app con `Main` un metodo è probabilmente un programma runnable. È possibile usare il modello Applicazione console per creare un progetto da usare con l'app Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Elenco di codice per un singolo file

1. Avviare Visual Studio e aprire un progetto applicazione console C# vuoto.
1. Sostituire tutto il codice nel file *con estensione cs* del progetto con il contenuto del file o dell'elenco di codice.
1. Rinominare il file *con estensione cs del* progetto in modo che corrisponda al nome del file di codice.

### <a name="several-code-listings-or-files-on-disk"></a>Diversi elenchi di codice o file su disco

1. Avviare Visual Studio e creare un nuovo progetto del tipo appropriato. Se non si è **certi,** usare l'applicazione console C#.
1. Nel nuovo progetto sostituire tutto il codice nel file di codice del progetto con il contenuto del primo elenco o file di codice.
1. Rinominare il file di codice del progetto in modo che corrisponda al nome del file di codice.
1. Per ogni file di codice rimanente:
   1. Fare clic con il pulsante destro del mouse sul nodo del **Esplora soluzioni** e scegliere Aggiungi elemento esistente oppure selezionare il progetto e  >  premere **MAIUSC** + **ALT** + **A.**
   1. Individuare e selezionare il file di codice per importarlo nel progetto.

### <a name="several-files-in-a-folder"></a>Diversi file in una cartella

Se si dispone di una cartella con molti file, verificare prima di tutto la presenza di un file di progetto o di soluzione. I programmi creati Visual Studio hanno file di progetto e soluzione. In Windows Esplora file cercare i file con estensione *csproj* o *sln.* Fare doppio clic sul file *con estensione csproj* per aprirlo in Visual Studio. Vedere [Iniziare da una Visual Studio o da un progetto.](#start-from-a-project)

Se il codice è di un altro ambiente di sviluppo, non è presente alcun file di progetto. Aprire la cartella scegliendo **Apri** cartella in  >  **Visual Studio.** Vedere [Sviluppare codice senza progetti o soluzioni.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="start-from-a-github-or-azure-devops-repo"></a>Iniziare da un GitHub o Azure DevOps di lavoro

Se il codice da eseguire si trova in un GitHub o Azure DevOps, è possibile usare Visual Studio per aprire il progetto direttamente dal repo. Vedere [Aprire un progetto da un repo.](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Eseguire il programma

Per iniziare a compilare il programma, premere il pulsante **Start** verde sulla barra Visual Studio oppure premere **F5** o **CTRL** + **F5.** Con il **pulsante Start** o **F5** viene eseguito il programma nel debugger.

Visual Studio tenta di compilare ed eseguire il codice nel progetto. Se una compilazione non riesce, vedere le sezioni seguenti per alcune idee su come ottenere il progetto per la compilazione corretta.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Il codice potrebbe contenere errori. In caso contrario, il codice potrebbe essere corretto, ma dipende da assembly mancanti o NuGet pacchetti o ha come destinazione una versione diversa di .NET. In questi casi, potrebbe essere possibile correggere facilmente la compilazione.

### <a name="add-references"></a>Aggiungere riferimenti

Per compilare correttamente, il codice deve essere corretto e avere i riferimenti corretti alle librerie o ad altre dipendenze. Le sottolineature ondulate rosse nel codice o nelle voci **nell'elenco** errori mostrano gli errori anche prima di compilare ed eseguire il programma. Se gli errori riguardano nomi non risolti, è probabile che sia necessario aggiungere un riferimento o una `using` direttiva o entrambi. Se il codice fa riferimento ad assembly o NuGet pacchetti mancanti, è necessario aggiungere tali riferimenti al progetto.

Visual Studio cerca di identificare i riferimenti mancanti. Quando un nome non viene risolto, nell'editor viene visualizzata un'icona a forma di lampadina. Selezionare la lampadina per visualizzare suggerimenti su come risolvere il problema. Le correzioni possono essere:

- Aggiungere una direttiva using.
- Aggiungere un riferimento a un assembly.
- Installare un NuGet pacchetto.

#### <a name="add-a-using-directive"></a>Aggiungere una direttiva using

Ecco un esempio di direttiva `using` mancante. È possibile aggiungere `using System;` all'inizio del file di codice per risolvere il nome non `Console` risolto:

::: moniker range="<=vs-2019"
![Screenshot della lampadina per aggiungere una direttiva using.](media/name-does-not-exist2.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/missing-using-directive.png" alt-text="Screenshot della lampadina per aggiungere una direttiva using." border="false":::
::: moniker-end

#### <a name="add-an-assembly-reference"></a>Aggiungere un riferimento all'assembly

I riferimenti .NET possono essere assembly o NuGet pacchetti. Nel codice sorgente, l'autore o l'autore in genere illustra gli assembly necessari per il codice e i pacchetti da cui dipende. Per aggiungere manualmente un riferimento a un  progetto, fare clic con il pulsante destro del mouse sul nodo Riferimenti **in** Esplora soluzioni scegliere **Aggiungi riferimento**. In **Gestione riferimenti individuare** e aggiungere l'assembly necessario.

::: moniker range="<=vs-2019"
![Screenshot del menu Aggiungi riferimento.](media/add-reference.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/add-reference.png" alt-text="Screenshot del menu Aggiungi riferimento." border="false":::
::: moniker-end

È possibile trovare assembly e aggiungere riferimenti seguendo le istruzioni riportate in Aggiungere o rimuovere [riferimenti tramite Gestione riferimenti](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="add-a-nuget-package"></a>Aggiungere un pacchetto NuGet

Se Visual Studio rileva un pacchetto NuGet, viene visualizzata una lampadina che offre la possibilità di installare il pacchetto:

::: moniker range="<=vs-2019"
![Screenshot di una lampadina per installare un pacchetto NuGet.](media/lightbulb-add-package.png)
::: moniker-end
::: moniker range=">=vs-2022"
:::image type="content" source="media/vs-2022/lightbulb-add-package.png" alt-text="Screenshot di una lampadina per installare un pacchetto NuGet." border="false":::
::: moniker-end

Se il problema non viene risolto o Visual Studio possibile individuare il pacchetto, provare a cercare il pacchetto online. Vedere [Installare e usare un pacchetto NuGet in Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

### <a name="use-the-right-version-of-net"></a>Usare la versione corretta di .NET

Poiché versioni diverse del .NET Framework hanno una certa compatibilità con le versioni precedenti, un framework più recente potrebbe eseguire codice scritto per un framework meno recente senza modifiche. In alcuni casi, tuttavia, è necessario impostare come destinazione una versione specifica di .NET Framework. Potrebbe essere necessario installare una versione specifica del .NET Framework o .NET Core. Vedere [Modificare Visual Studio](../../install/modify-visual-studio.md).

Per modificare la versione di .NET Framework di destinazione, vedere [Modificare il framework di destinazione](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Per altre informazioni, vedere [Risoluzione dei .NET Framework errori di destinazione](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Passaggi successivi

- Esplorare l'Visual Studio di sviluppo locale leggendo [Benvenuti nell'IDE Visual Studio .](../visual-studio-ide.md)
- [Creare la prima app C#.](tutorial-console.md)
