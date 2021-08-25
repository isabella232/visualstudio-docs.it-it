---
title: Come eseguire un programma (C#)
description: Guida per principianti su come eseguire un programma C# in Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 08/24/2021
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
ms.openlocfilehash: e2a5e2997a15f3d91c9a12d3aff5c1d1e31aff90
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785923"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Procedura: Eseguire un programma C# in Visual Studio

Le attività da eseguire per eseguire un programma dipendono dall'origine, dal tipo di programma, dall'app o dal servizio e dal fatto che si voglia eseguirlo o meno nel debugger. Nel caso più semplice, quando un progetto è aperto in Visual Studio, compilarlo ed eseguirlo premendo + **CTRL F5** ( Avvia senza eseguire debug ) o **F5** (**Avvia** con debug ) o premere la freccia verde (**Pulsante** Start ) sulla barra degli strumenti principale Visual Studio.

![Screenshot che mostra il pulsante Start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>A partire da un progetto

Se si dispone di un progetto C# (file *con estensione csproj),* è possibile eseguirlo, se si tratta di un programma runnable. Se un progetto contiene un file C# con un metodo e il relativo output è un eseguibile (EXE), molto probabilmente verrà eseguito se viene `Main` compilato correttamente.

Se il codice per il programma è già presente in un progetto in Visual Studio, aprire il progetto. Per aprire il progetto, fare doppio clic o toccare il file con estensione *csproj* dal Windows Esplora file o da Visual Studio, scegliere Apri un **progetto,** individuare il file di progetto ( con estensione *csproj)* e scegliere il file di progetto.

Dopo il caricamento dei progetti Visual Studio, premere **CTRL** + **F5** ( Avvia senza eseguire debug ) o usare il pulsante **Start** verde sulla barra degli strumenti Visual Studio per eseguire il programma.  Se sono presenti più progetti, quello con il metodo deve `Main` essere impostato come progetto di avvio. Per impostare il progetto di avvio, fare clic con il pulsante destro del mouse su un nodo di progetto e scegliere **Imposta come progetto di avvio**.

![Impostare il progetto di avvio](media/set-as-startup-project.png)

Visual Studio tenta di compilare ed eseguire il progetto.  Se si verificano errori di compilazione, l'output di compilazione viene visualizzato nella finestra **Output** e gli errori nella **finestra Elenco** errori.

Se la compilazione ha esito positivo, l'app viene eseguita in modo appropriato per il tipo di progetto. Le app console vengono eseguite in una finestra del terminale, Windows le app desktop vengono avviate in una nuova finestra, le app Web vengono avviate nel browser (ospitate da IIS Express) e così via.

## <a name="starting-from-code"></a>A partire dal codice

Se si inizia da un elenco di codice, da un file di codice o da un numero ridotto di file, assicurarsi innanzitutto che il codice da eseguire sia da un'origine attendibile e che sia un programma eseguibile. Se ha un metodo, è probabilmente inteso come programma runnable che è possibile usare il modello App console per creare un progetto da usare in `Main` Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Elenco di codice per un singolo file

Avviare Visual Studio, aprire un progetto console C# vuoto, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Incollare quindi il contenuto del codice nel file con estensione cs. Quando si incolla il codice, sovrascrivere o eliminare il codice presente in precedenza. Rinominare il file in modo che corrisponda al codice originale.

### <a name="code-listings-for-a-few-files"></a>Elenchi di codice per alcuni file

Avviare Visual Studio, aprire un progetto console C# vuoto, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Incollare quindi il contenuto del primo file di codice nel file con estensione cs. Rinominare il file in modo che corrisponda al codice originale. 

Per un secondo file, fare clic con il pulsante destro del mouse sul nodo del progetto **in Esplora soluzioni** per aprire il menu di scelta rapida per il progetto e scegliere Aggiungi elemento esistente **>** (oppure usare la combinazione di tasti MAIUSC ALT A ) e selezionare i file di +  + codice.

### <a name="multiple-files-on-disk"></a>Più file su disco

1. Creare un nuovo progetto del tipo appropriato (se non si è certi di usare **l'app console** C#).

2. Fare clic con il pulsante destro del mouse sul nodo del progetto, scegliere **Aggiungi**  >  **elemento** esistente per selezionare i file e importarli nel progetto.  

### <a name="starting-from-a-folder"></a>A partire da una cartella

Quando si lavora con una cartella di molti file, verificare innanzitutto se è presente un progetto o una soluzione.  Se il programma è stato creato con Visual Studio, è necessario trovare un file di progetto o di soluzione. Cercare i file con estensione *csproj* o sln e nel Windows Esplora file fare doppio clic su uno di essi per aprirli in Visual Studio. Vedere [A partire da una Visual Studio o da un progetto](#starting-from-a-project).

Se non si ha un file di progetto, ad esempio se il codice è stato sviluppato  in un altro ambiente di sviluppo, aprire la cartella di primo livello usando il metodo Apri cartella in Visual Studio. Vedere [Sviluppare codice senza progetti o soluzioni.](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="starting-from-a-github-or-azure-devops-repo"></a>A partire da un GitHub o Azure DevOps dati

Se il codice da eseguire si trova in GitHub o in un Azure DevOps, è possibile usare Visual Studio per aprire il progetto direttamente dal repo. Vedere [Aprire un progetto da un repo.](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Eseguire il programma

Per avviare il programma, premere la freccia verde (pulsante **Start)** sulla barra degli strumenti principale Visual Studio oppure premere **F5** o **CTRL** + **F5** per eseguire il programma. Quando si usa il **pulsante Avvia,** viene eseguito nel debugger.  Visual Studio tenta di compilare il codice nel progetto ed eseguirlo.  Se l'operazione ha esito positivo, è ottimo. In caso contrario, continuare a leggere alcune idee su come ottenerlo per la compilazione corretta.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Il codice potrebbe avere errori, ma se il codice è corretto, ma dipende solo da altri assembly o pacchetti NuGet o è stato scritto per una versione diversa di .NET, è possibile correggerlo facilmente.

### <a name="add-references"></a>Aggiungere riferimenti

Per compilare correttamente, il codice deve essere corretto e avere i riferimenti corretti impostati per le librerie o altre dipendenze. È possibile esaminare le righe rosse ondulate e l'Elenco errori per verificare se il programma presenta errori, anche prima di compilarlo ed eseguirlo.  Se vengono visualizzati errori correlati a nomi non risolti, è probabile che sia necessario aggiungere un riferimento o una direttiva using o entrambi. Se il codice fa riferimento ad assembly o NuGet pacchetti, è necessario aggiungere tali riferimenti nel progetto.

Visual Studio di identificare i riferimenti mancanti. Quando un nome non viene risolto, nell'editor viene visualizzata un'icona a forma di lampadina. Se si fa clic sulla lampadina, è possibile visualizzare alcuni suggerimenti su come risolvere il problema. Le correzioni possono essere:

- aggiungere una direttiva using
- aggiungere un riferimento a un assembly oppure
- installare un NuGet pacchetto.

#### <a name="missing-using-directive"></a>Direttiva using mancante

Ad esempio, nella schermata seguente è possibile scegliere di aggiungere all'inizio del file di codice per `using System;` risolvere il nome non `Console` risolto:

![Screenshot della lampadina per aggiungere una direttiva using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Riferimento all'assembly mancante

I riferimenti .NET possono essere sotto forma di assembly o NuGet pacchetti. In genere, se si trova codice sorgente, l'autore o l'autore spiega quali assembly sono necessari e da quali pacchetti dipende il codice. Per aggiungere manualmente un riferimento a un  progetto, fare clic con il pulsante destro del mouse sul nodo Riferimenti nel **Esplora soluzioni**, scegliere **Aggiungi** riferimento e individuare l'assembly richiesto.

![Screenshot del menu Aggiungi riferimento](media/add-reference.png)

È possibile trovare assembly e aggiungere riferimenti seguendo le istruzioni riportate in Aggiungere o rimuovere [riferimenti tramite Gestione riferimenti](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Pacchetto NuGet mancante

Se Visual Studio rileva un pacchetto NuGet mancante, viene visualizzata una lampadina che offre la possibilità di installarlo:

![Screenshot della lampadina per installare il pacchetto](media/lightbulb-add-package.png)

Se il problema non viene risolto e Visual Studio possibile individuare il pacchetto, provare a cercarlo online. Vedere [Installare e usare un pacchetto NuGet in Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Usare la versione corretta di .NET

Poiché versioni diverse del .NET Framework hanno un certo grado di compatibilità con le versioni precedenti, un framework più recente potrebbe eseguire codice scritto per un framework meno recente senza alcuna modifica. Tuttavia, a volte è necessario scegliere come destinazione un framework specifico. Potrebbe essere necessario installare una versione specifica del .NET Framework o .NET Core, se non è già installata. Vedere [Modificare Visual Studio](../../install/modify-visual-studio.md).

Per modificare il framework di destinazione, vedere [Modificare il framework di destinazione.](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version) Per altre informazioni, vedere [Risoluzione dei .NET Framework di destinazione](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)degli errori .

## <a name="next-steps"></a>Passaggi successivi

Esplorare l'Visual Studio di sviluppo locale [leggendo Benvenuti nell'IDE Visual Studio .](../visual-studio-ide.md)

## <a name="see-also"></a>Vedi anche

[Creare la prima app C#](tutorial-console.md)
