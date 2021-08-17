---
title: Opzioni della riga di comando devenv
description: Informazioni sulle opzioni della riga di comando devenv e su come usarle per impostare le opzioni IDE e anche compilare, eseguire il debug e distribuire progetti, il tutto dalla riga di comando.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: fbad39c210c5cefd45dfbdfa9bec8f6cafe432cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034318"
---
# <a name="devenv-command-line-switches"></a>Opzioni della riga di comando devenv

Devenv consente di impostare varie opzioni per l'ambiente IDE, compilare i progetti, eseguire il debug dei progetti e distribuire i progetti dalla riga di comando. Usare queste opzioni per eseguire l'IDE da uno script o un file con estensione bat, ad esempio uno script di compilazione notturna, o per avviare l'IDE in una configurazione particolare.

> [!NOTE]
> Per le attività relative alla compilazione, è consigliabile usare MSBuild anziché devenv. Per altre informazioni, vedere [Riferimenti alla riga di comando di MSBuild](../../msbuild/msbuild-command-line-reference.md).

Per informazioni sulle opzioni correlate allo sviluppo di VSPackage, vedere anche [Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Sintassi delle opzioni devenv

I comandi che iniziano con `devenv` vengono gestiti dall'utilità `devenv.com`, che restituisce l'output tramite flussi di sistema standard come `stdout` e `stderr`. L'utilità determina il reindirizzamento I/O appropriato durante l'acquisizione dell'output, ad esempio in un file con estensione txt.

In alternativa, i comandi che iniziano con `devenv.exe` possono usare le stesse opzioni, ma l'utilità `devenv.com` viene ignorata. L'uso di `devenv.exe` impedisce direttamente la visualizzazione dell'output nella console.

Le regole di sintassi per le opzioni `devenv` sono simili alle regole per altre utilità della riga di comando DOS. Le regole di sintassi seguenti si applicano a tutte le opzioni `devenv` e ai relativi argomenti:

- I comandi iniziano con `devenv`.

- Le opzioni non distinguono tra maiuscole e minuscole.

- È possibile specificare un'opzione con un trattino ("-") o una barra rovesciata ("/").

- Quando si specifica una soluzione o un progetto, il primo argomento è il nome del file di soluzione o file di progetto, incluso il percorso del file.

- Se il primo argomento è un file che non è una soluzione o un progetto, tale file viene aperto nell'editor appropriato, in una nuova istanza dell'IDE.

- Quando si specifica un nome di file di progetto anziché un nome di file di soluzione, un comando `devenv` cerca nella cartella padre del file di progetto un file di soluzione con lo stesso nome. Ad esempio, il comando `devenv myproject1.vbproj /build` cerca nella cartella padre un file di soluzione denominato `myproject1.sln`.

  > [!NOTE]
  > Nella cartella padre deve trovarsi un solo e unico file che faccia riferimento a questo progetto. Se la cartella padre non contiene alcun file di soluzione che fa riferimento a questo progetto, o se la cartella padre contiene due o più file di soluzione che vi fanno riferimento, viene creato un file di soluzione temporaneo.

- Quando i percorsi e i nomi dei file contengono spazi, è necessario racchiuderli tra virgolette (""). Ad esempio, `"c:\project a\"`.

- Inserire uno spazio tra le opzioni e gli argomenti sulla stessa riga. Ad esempio, il comando `devenv /log output.txt` apre l'IDE e restituisce tutte le informazioni di log per la sessione in output.txt.

- Nei comandi `devenv` non può essere usata la sintassi di corrispondenza dei modelli.

## <a name="devenv-switches"></a>Opzioni devenv

Le opzioni della riga di comando seguenti consentono di visualizzare l'IDE ed eseguire l'attività descritta.

|Switch della riga di comando|Descrizione|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Avvia l'IDE ed esegue il comando specificato.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Carica un eseguibile C++ sotto il controllo del debugger. Questa opzione non è disponibile per gli eseguibili Visual Basic o C#. Per altre informazioni, vedere [Automatically start a process in the debugger](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger) (Avviare automaticamente un processo nel debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Confronta due file. Accetta quattro parametri: *SourceFile*, *TargetFile*, *SourceDisplayName* (facoltativo) e *TargetDisplayName* (facoltativo).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Apre la soluzione specificata senza caricare progetti.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Apre i file specificati in un'istanza dell'applicazione in esecuzione. Se non sono presenti istanze in esecuzione, viene avviata una nuova istanza con un layout di finestra semplificato.<br /><br /> `devenv /edit File1 File2`|
|[/LCID o /L](lcid-devenv-exe.md)|Imposta la lingua predefinita per l'IDE. Se la lingua specificata non è inclusa nell'installazione di Visual Studio, questa impostazione viene ignorata.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Avvia Visual Studio e registra tutte le attività nel file di registro.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|L'ambiente IDE viene aperto senza visualizzare la schermata iniziale.<br /><br /> `devenv /nosplash File1 File2`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Ripristina impostazioni predefinite di Visual Studio. Facoltativamente reimposta le impostazioni nel file con estensione `.vssettings` specificato.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Run o /R](run-devenv-exe.md)|Compila ed esegue la soluzione specificata.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Compila ed esegue la soluzione specificata, riduce a icona l'IDE quando la soluzione viene eseguita e chiude l'IDE al termine dell'esecuzione della soluzione.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Avvia Visual Studio in modalità sicura. Questa opzione carica solo l'ambiente predefinito, i servizi predefiniti e le versioni acquistate di pacchetti di terze parti.<br /><br /> Questa opzione non accetta argomenti.|
|[/UseEnv](useenv-devenv-exe.md)|Fa sì che l'IDE usi le variabili di ambiente PATH, INCLUDE, LIBPATH e LIB per la compilazione C++. Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++**. Per altre informazioni, vedere [Impostare le variabili di percorso e di ambiente per le compilazioni da riga di comando](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

Le opzioni della riga di comando seguenti non visualizzano l'IDE.

|Switch della riga di comando|Descrizione|
| - |-----------------|
|[/?](q-devenv-exe.md)|Visualizza la Guida per le opzioni `devenv` nella **finestra del prompt dei comandi**.<br /><br /> Questa opzione non accetta argomenti.|
|[/Build](build-devenv-exe.md)|Compila la soluzione o il progetto specificati in base alla configurazione relativa.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Elimina i file creati dal comando di compilazione, senza che ciò abbia effetto sui file di origine.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Compila la soluzione, in base alla configurazione relativa, insieme ai file necessari per la distribuzione.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Consente di specificare un file per la ricezione di errori durante la compilazione.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|Il progetto da compilare, pulire o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione `/Build`, `/Rebuild`, `/Clean` o `/Deploy`.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Specifica la configurazione del progetto da compilare o distribuire. È possibile usare questa opzione solo se è stata specificata anche l'opzione `/Project`.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Pulisce e compila la soluzione o il progetto specificati in base alla configurazione relativa.<br /><br /> `devenv mysln.sln /rebuild`|
|[/Upgrade](upgrade-devenv-exe.md)|Aggiorna il file di soluzione specificato e tutti i file di progetto relativi, o il file di progetto specificato, nei formati Visual Studio correnti per tali file.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Vedi anche

- [Generale, Ambiente, finestra di dialogo Opzioni](general-environment-options-dialog-box.md)
- [Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
