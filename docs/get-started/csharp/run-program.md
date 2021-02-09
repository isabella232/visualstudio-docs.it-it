---
title: Come eseguire un programma (C#)
description: Guida per principianti su come eseguire un programma C# in Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
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
ms.openlocfilehash: bbebcec3f5b2de01bcbfa7839f68e6f7a3e2cc64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922844"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Procedura: eseguire un programma C# in Visual Studio

Ciò che è necessario fare per eseguire un programma dipende da ciò che si sta iniziando, dal tipo di programma, dall'app o dal servizio e dal fatto che si desideri eseguirlo nel debugger. Nel caso più semplice, quando si apre un progetto in Visual Studio, compilarlo ed eseguirlo premendo **CTRL** + **F5** (**Avvia senza eseguire debug**) o **F5** (**Avvia con debug**) o premere la freccia verde (**pulsante Avvia**) sulla barra degli strumenti principale di Visual Studio.

![Screenshot che mostra il pulsante avvia](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Avvio da un progetto

Se si dispone di un progetto C# (file con estensione *csproj* ), è possibile eseguirlo, se si tratta di un programma eseguibile. Se un progetto contiene un file C# con un `Main` metodo e l'output è un file eseguibile (exe), è molto probabile che venga eseguito se viene compilato correttamente.

Se si dispone già del codice per il programma in un progetto in Visual Studio, aprire il progetto. Per aprire il progetto, fare doppio clic o toccare il file con *estensione csproj* da Esplora file di Windows o da Visual Studio, scegliere **Apri un progetto**, Sfoglia per trovare il file di progetto (con *estensione csproj*) e scegliere il file di progetto.

Al termine del caricamento dei progetti in Visual Studio, premere **CTRL** + **F5** (**Avvia senza eseguire debug**) o usare il pulsante di **avvio** verde sulla barra degli strumenti di Visual Studio per eseguire il programma.  Se sono presenti più progetti, `Main` è necessario impostare quello con il metodo come progetto di avvio. Per impostare il progetto di avvio, fare clic con il pulsante destro del mouse su un nodo di progetto e scegliere **Imposta come progetto di avvio**.

![Imposta progetto di avvio](media/set-as-startup-project.png)

Visual Studio tenta di compilare ed eseguire il progetto.  Se sono presenti errori di compilazione, l'output di compilazione nella finestra di **output** e gli errori vengono visualizzati nella finestra **Elenco errori** .

Se la compilazione ha esito positivo, l'app viene eseguita in modo appropriato per il tipo di progetto. Le app console vengono eseguite in una finestra del terminale, le app desktop di Windows vengono avviate in una nuova finestra, le app Web vengono avviate nel browser (ospitate da IIS Express) e così via.

## <a name="starting-from-code"></a>Avvio dal codice

Se si inizia da un listato di codice, da un file di codice o da un numero ridotto di file, assicurarsi prima di tutto che il codice che si vuole eseguire provenga da un'origine attendibile e che sia un programma eseguibile. Se dispone di un `Main` metodo, è probabile che sia destinato a un programma eseguibile che è possibile usare con il modello di applicazione console per creare un progetto da usare in Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Listato di codice per un singolo file

Avviare Visual Studio, aprire un progetto console C# vuoto, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Incollare quindi il contenuto del codice nel file con estensione cs. Quando si incolla il codice, sovrascrivere o eliminare il codice precedente. Rinominare il file in modo che corrisponda al codice originale.

### <a name="code-listings-for-a-few-files"></a>Elenchi di codice per alcuni file

Avviare Visual Studio, aprire un progetto console C# vuoto, selezionare tutto il codice nel file con estensione cs già presente nel progetto ed eliminarlo. Incollare quindi il contenuto del primo file di codice nel file con estensione cs. Rinominare il file in modo che corrisponda al codice originale. 

Per un secondo file, fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** per aprire il menu di scelta rapida per il progetto e scegliere **Aggiungi > elemento esistente** (oppure utilizzare la combinazione di tasti **MAIUSC** + **ALT** + **a**) e selezionare i file di codice.

### <a name="multiple-files-on-disk"></a>Più file su disco

1. Creare un nuovo progetto del tipo appropriato (usare l' **app console** C# se non si è certi).

2. Fare clic con il pulsante destro del mouse sul nodo del progetto, se **Aggiungi**  >  **elemento esistente** per selezionare i file e importarli nel progetto.  

### <a name="starting-from-a-folder"></a>Avvio da una cartella

Quando si lavora con una cartella di molti file, verificare prima di tutto se è presente un progetto o una soluzione.  Se il programma è stato creato con Visual Studio, dovrebbe essere presente un file di progetto o un file di soluzione. Cercare i file con estensione *. csproj* o. sln e in Esplora file di Windows, fare doppio clic su uno di essi per aprirli in Visual Studio. Vedere [a partire da una soluzione o da un progetto di Visual Studio](#starting-from-a-project).

Se non si dispone di un file di progetto, ad esempio se il codice è stato sviluppato in un altro ambiente di sviluppo, aprire la cartella di livello superiore usando il metodo **Apri cartella** in Visual Studio. Vedere [sviluppare codice senza progetti o soluzioni](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>A partire da un repository GitHub o Azure DevOps

Se il codice che si vuole eseguire si trova in GitHub o in un repository di Azure DevOps, è possibile usare Visual Studio per aprire il progetto direttamente dal repository. Vedere [aprire un progetto da un repository](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Eseguire il programma

Per avviare il programma, premere la freccia verde (pulsante **Avvia** ) sulla barra degli strumenti principale di Visual Studio oppure premere **F5** o **CTRL** + **F5** per eseguire il programma. Quando si usa il pulsante **Avvia** , viene eseguito nel debugger.  Visual Studio tenta di compilare il codice nel progetto ed eseguirlo.  Se l'operazione ha esito positivo, In caso contrario, continuare a leggere per alcune idee su come ottenere la compilazione corretta.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Il codice potrebbe avere errori, ma se il codice è corretto, ma dipende solo da altri assembly o pacchetti NuGet oppure è stato scritto per essere destinato a una versione diversa di .NET, potrebbe essere possibile correggerlo facilmente.

### <a name="add-references"></a>Aggiungere riferimenti

Per la corretta compilazione, è necessario che il codice sia corretto e che i riferimenti corretti siano configurati per le librerie o altre dipendenze. È possibile esaminare le linee ondulate rosse e **Elenco errori** per verificare se il programma contiene errori, anche prima di compilarlo ed eseguirlo. Se vengono visualizzati errori correlati a nomi non risolti, è probabile che sia necessario aggiungere un riferimento o una direttiva using o entrambi. Se il codice fa riferimento a tutti gli assembly o a pacchetti NuGet, è necessario aggiungere tali riferimenti nel progetto.

Visual Studio tenta di semplificare l'identificazione di riferimenti mancanti. Quando un nome non è risolto, nell'editor viene visualizzata un'icona a bulbo chiaro. Se si fa clic sulla lampadina, è possibile visualizzare alcuni suggerimenti su come risolvere il problema. Le correzioni potrebbero essere:

- aggiungere una direttiva using
- aggiungere un riferimento a un assembly o
- installare un pacchetto NuGet.

#### <a name="missing-using-directive"></a>Direttiva using mancante

Ad esempio, nella schermata seguente è possibile scegliere di aggiungere `using System;` all'inizio del file di codice per risolvere il nome non risolto `Console` :

![Screenshot della lampadina per aggiungere una direttiva using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Riferimento all'assembly mancante

I riferimenti .NET possono essere sotto forma di assembly o pacchetti NuGet. In genere, se si trova il codice sorgente, il server di pubblicazione o l'autore descrivono quali assembly sono necessari e quali pacchetti dipendono dal codice. Per aggiungere manualmente un riferimento a un progetto, fare clic con il pulsante destro del mouse sul nodo **riferimenti** nel **Esplora soluzioni**, scegliere **Aggiungi riferimento** e individuare l'assembly richiesto.

![Screenshot del menu Aggiungi riferimento](media/add-reference.png)

È possibile trovare gli assembly e aggiungere riferimenti seguendo le istruzioni riportate in [aggiungere o rimuovere riferimenti tramite Gestione riferimenti](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Pacchetto NuGet mancante

Se Visual Studio rileva un pacchetto NuGet mancante, viene visualizzata una lampadina che offre la possibilità di installarla:

![Screenshot della lampadina per installare il pacchetto](media/lightbulb-add-package.png)

Se il problema persiste e Visual Studio non è in grado di individuare il pacchetto, provare a cercarlo online. Vedere [installare e usare un pacchetto NuGet in Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Usare la versione corretta di .NET

Poiché versioni diverse del .NET Framework hanno un certo grado di compatibilità con le versioni precedenti, un Framework più recente può eseguire codice scritto per un Framework precedente senza alcuna modifica. Tuttavia, a volte è necessario fare riferimento a un Framework specifico. Potrebbe essere necessario installare una versione specifica di .NET Framework o .NET Core, se non è già installato. Vedere [modificare Visual Studio](../../install/modify-visual-studio.md).

Per modificare il Framework di destinazione, vedere [modificare il Framework di destinazione](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Per ulteriori informazioni, vedere [risoluzione dei problemi .NET Framework destinazione degli errori](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Passaggi successivi

Esplorare l'ambiente di sviluppo di Visual Studio leggendo [Benvenuti nell'IDE di Visual Studio](../visual-studio-ide.md).

## <a name="see-also"></a>Vedi anche

[Creare la prima app C#](tutorial-console.md)
