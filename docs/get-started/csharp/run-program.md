---
title: Come eseguire un programma in C
description: Guida per principianti su come eseguire un programma in C.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ffe52fc2bf7d05084307b4d972e45f4b1d2acdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "76924616"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Procedura: eseguire un programma in Visual Studio

Le operazioni da eseguire per eseguire un programma dipendono da cosa si sta iniziando, dal tipo di programma, app o servizio che si tratta e dal fatto che si desideri eseguirlo nel debugger o meno. Nel caso più semplice, quando un progetto è aperto in Visual Studio, compilarlo ed eseguirlo premendo **Ctrl**+**F5** (**Avvia senza eseguire debug**) o **F5** (**Inizia con il debug**) oppure premere la freccia verde (**Pulsante Start**) sulla barra degli strumenti principale di Visual Studio.

![Schermata che mostra il pulsante Start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Partendo da un progetto

Se si dispone di un progetto di C , ovvero*file con estensione csproj* , è possibile eseguirlo, se si tratta di un programma eseguibile. Se un progetto contiene un `Main` file di C, con un metodo e il relativo output è un eseguibile (EXE), molto probabilmente verrà eseguito se viene compilato correttamente.

Se si dispone già del codice per il programma in un progetto in Visual Studio, aprire il progetto. Per aprire il progetto, fare doppio clic o toccare il *file con estensione csproj* da Esplora file di Windows oppure in Visual Studio scegliere **Apri progetto,** Individua il file del progetto (*con estensione csproj)* e scegliere il file di progetto.

Dopo il caricamento dei progetti in Visual Studio, premere **CTRL**+**F5** (**Avvia senza eseguire debug**) oppure utilizzare il pulsante Start verde sulla barra degli strumenti di Visual Studio per eseguire il programma. **Start**  Se sono presenti più progetti, `Main` quello con il metodo deve essere impostato come progetto di avvio. Per impostare il progetto di avvio, fare clic con il pulsante destro del mouse sul nodo di un progetto e scegliere Imposta come progetto di **avvio**.

![Imposta progetto di avvio](media/set-as-startup-project.png)

Visual Studio tenta di compilare ed eseguire il progetto.  Se sono presenti errori di compilazione, l'output di compilazione viene visualizzato nella finestra **Output** e gli errori nella finestra **Elenco errori.**

Se la compilazione ha esito positivo, l'app viene eseguita in modo appropriato per il tipo di progetto. Le app console vengono eseguite in una finestra terminale, le app desktop di Windows vengono avviate in una nuova finestra, le app Web vengono avviate nel browser (ospitato da IIS Express) e così via.

## <a name="starting-from-code"></a>A partire dal codice

Se si inizia da un elenco di codice, da un file di codice o da un numero ridotto di file, assicurarsi innanzitutto che il codice che si desidera eseguire provenga da una fonte attendibile ed è un programma eseguibile. Se dispone `Main` di un metodo, è probabile che sia inteso come un programma eseguibile che è possibile utilizzare il modello App console per creare un progetto da utilizzare in Visual Studio.If it has a method, it is likely intended as a runnable program that you can use the Console App template to create a project to work with it in Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Elenco di codice per un singolo file

Avviare Visual Studio, aprire un progetto di console vuoto di C, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Quindi, incollare il contenuto del codice nel file con estensione cs. Quando si incolla il codice, sovrascrivere o eliminare il codice che era presente in precedenza. Rinominare il file in modo che corrisponda al codice originale.

### <a name="code-listings-for-a-few-files"></a>Elenchi di codice per alcuni file

Avviare Visual Studio, aprire un progetto di console vuoto di C, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Quindi, incollare il contenuto del primo file di codice nel file con estensione cs. Rinominare il file in modo che corrisponda al codice originale. 

Per un secondo file, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** per aprire il menu di scelta rapida per il progetto e scegliere **Aggiungi > elemento esistente** (oppure utilizzare la combinazione di tasti **Maiusc**+**Alt**+**A**) e selezionare i file di codice.

### <a name="multiple-files-on-disk"></a>Più file su disco

1. Creare un nuovo progetto del tipo appropriato (utilizzare **l'app console** di C , se non si è sicuri).

2. Fare clic con il pulsante destro del mouse sul nodo del progetto, selezionare **Aggiungi** > **elemento esistente** per selezionare i file e importarli nel progetto.  

### <a name="starting-from-a-folder"></a>Avvio da una cartella

Quando si lavora con una cartella di molti file, verificare innanzitutto se è presente un progetto o una soluzione.  Se il programma è stato creato con Visual Studio, è necessario trovare un file di progetto o un file di soluzione. Cercare i file con *estensione csproj* o sln e in Esplora file di Windows, fare doppio clic su uno di essi per aprirli in Visual Studio. Vedere [Avvio da una soluzione o da un progetto](#starting-from-a-project)di Visual Studio.

Se non si dispone di un file di progetto, ad esempio se il codice è stato sviluppato in un altro ambiente di sviluppo, aprire la cartella di primo livello utilizzando il **Apri metodo cartella** in Visual Studio.If you don't have a project file, such as if the code was developed in another development environment, then open the top-level folder by using the Open folder method in Visual Studio. Consultate [Sviluppare codice senza progetti o soluzioni.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="starting-from-a-github-or-azure-devops-repo"></a>A partire da un repo GitHub o DevOps di AzureStarting from a GitHub or Azure DevOps repo

Se il codice che si vuole eseguire è in GitHub o in un repository DevOps di Azure, è possibile usare Visual Studio per aprire il progetto direttamente dal repository. Consultate [Aprire un progetto da un repository.](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Eseguire il programma

Per avviare il programma, premere la freccia verde (pulsante**Start)** sulla barra degli strumenti principale di Visual Studio oppure premere **F5** o **Ctrl**+**F5** per eseguire il programma. Quando si utilizza il pulsante **Start** , viene eseguito sotto il debugger.  Visual Studio tenta di compilare il codice nel progetto ed eseguirlo.  Se questo ha successo, grande! Ma se no, continua a leggere per alcune idee su come farlo costruire con successo.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Il codice potrebbe avere errori, ma se il codice è corretto, ma dipende solo da alcuni altri assembly o pacchetti NuGet o è stato scritto per una versione diversa di .NET, potrebbe essere possibile risolvere facilmente il problema.

### <a name="add-references"></a>Aggiungere riferimenti

Per eseguire correttamente la compilazione, il codice deve essere corretto e avere i riferimenti corretti impostati per librerie o altre dipendenze. È possibile esaminare le linee ondulate rosse e **l'Elenco errori** per vedere se il programma presenta errori, anche prima di compilarlo ed eseguirlo. Se vengono visualizzati errori relativi a nomi non risolti, è probabile che sia necessario aggiungere un riferimento o una direttiva using o entrambi. Se il codice fa riferimento a assembly o pacchetti NuGet, è necessario aggiungerli nel progetto.

Visual Studio tenta di identificare i riferimenti mancanti. Quando un nome non è risolto, nell'editor viene visualizzata un'icona a forma di lampadina. Se si fa clic sulla lampadina, è possibile visualizzare alcuni suggerimenti su come risolvere il problema. Le correzioni potrebbero essere:

- aggiungere una direttiva using
- aggiungere un riferimento a un assieme, o
- installare un pacchetto NuGet.

#### <a name="missing-using-directive"></a>Direttiva using mancante

Ad esempio, nella schermata seguente, `using System;` è possibile scegliere di aggiungere all'inizio `Console`del file di codice per risolvere il nome non risolto :

![Screenshot della lampadina per aggiungere una direttiva using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Riferimento all'assembly mancante

I riferimenti .NET possono essere sotto forma di assembly o pacchetti NuGet..........I riferimenti .NET can be in the form of assemblies or NuGet packages. In genere, se si trova il codice sorgente, l'editore o l'autore spiegherà quali assembly sono obbligatori e da quali pacchetti dipende il codice. Per aggiungere manualmente un riferimento a un progetto, fare clic con il pulsante destro del mouse sul nodo **Riferimenti** in **Esplora soluzioni,** scegliere **Aggiungi riferimento**e individuare l'assembly richiesto.

![Screenshot del menu Aggiungi riferimento](media/add-reference.png)

Per trovare assembly e riferimenti, seguire le istruzioni in [Aggiungere o rimuovere riferimenti utilizzando il gestore](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)dei riferimenti .

#### <a name="missing-nuget-package"></a>Pacchetto NuGet mancante

Se Visual Studio rileva un pacchetto NuGet mancante, viene visualizzata una lampadina che offre la possibilità di installarlo:

![Screenshot della lampadina per installare il pacchetto](media/lightbulb-add-package.png)

Se il problema persiste e Visual Studio non riesce a individuare il pacchetto, provare a cercarlo online. Vedere [Installare e utilizzare un pacchetto NuGet in Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Utilizzare la versione corretta di .NET

Poiché le diverse versioni di .NET Framework hanno un certo grado di compatibilità con le versioni precedenti, un framework più recente potrebbe eseguire codice scritto per un framework precedente senza alcuna modifica. Tuttavia, a volte è necessario impostare come destinazione un framework specifico. Potrebbe essere necessario installare una versione specifica di .NET Framework o .NET Core, se non è già installato. Vedere [Modifica di Visual Studio](../../install/modify-visual-studio.md).

Per modificare il framework di destinazione, vedere [Modificare il framework](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)di destinazione . Per ulteriori informazioni, vedere [Risoluzione dei problemi](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)relativi agli errori di destinazione di .NET Framework .

## <a name="next-steps"></a>Passaggi successivi

Esplorare l'ambiente di sviluppo di Visual Studio leggendo [Benvenuti nell'IDE](../visual-studio-ide.md)di Visual Studio .

## <a name="see-also"></a>Vedere anche

[Creare la prima app C#](tutorial-console.md)
