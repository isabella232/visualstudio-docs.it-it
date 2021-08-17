---
title: Personalizzare le attività di debug della compilazione con i file JSON
description: Informazioni su come personalizzare le attività per fornire alcuni dettagli di configurazione per eseguire ed eseguire il debug di una codebase Visual Studio non riconosce.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d05ffcc5140edcf04dd03b591df100831304fc6b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049025"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>Personalizzare le attività di compilazione e debug per lo sviluppo con "Apri cartella"

Visual Studio riconosce automaticamente molti linguaggi e codebase diversi per l'esecuzione, ma non tutti. Se si [apre una cartella di codice](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) in Visual Studio e Visual Studio sa come eseguire il codice, è possibile eseguirlo immediatamente senza ulteriori configurazioni.

Se la codebase usa strumenti di compilazione personalizzati non riconosciuti da Visual Studio, è necessario specificare alcuni dettagli di configurazione per eseguire il codice e gestirne il debug in Visual Studio. Per indicare a Visual Studio come compilare il codice, occorre definire *attività di compilazione*. È possibile creare una o più attività di compilazione per specificare tutti gli elementi necessari per compilare ed eseguire il codice di un linguaggio. È anche possibile creare attività arbitrarie che possono eseguire praticamente qualsiasi operazione. Ad esempio, si può creare un'attività per elencare il contenuto di una cartella o rinominare un file.

Personalizzare la codebase senza progetto con i seguenti file *json*:

|Nome file|Scopo|
|-|-|
|*tasks.vs.json*|Specificare i comandi di compilazione e le opzioni del compilatore personalizzati, nonché le attività arbitrarie (non correlate alla compilazione).<br>Accessibile tramite il comando **Configura attività** nel menu di scelta rapida di **Esplora soluzioni**.|
|*launch.vs.json*|Specificare gli argomenti della riga di comando per il debug.<br>Accessibile tramite il comando **Impostazioni per debug e avvio** nel menu di scelta rapida di **Esplora soluzioni**.|

Questi file *json* si trovano in una cartella nascosta denominata *.vs* nella cartella radice della codebase. I file *tasks.vs.json* e *launch.vs.json* vengono creati da Visual Studio all'occorrenza, quando di sceglie il comando **Configura attività** o **Impostazioni per debug e avvio** per un file o una cartella in **Esplora soluzioni**. Questi file *json* sono nascosti in quanto la maggior parte degli utenti preferisce in genere non archiviarli nel controllo del codice sorgente. Tuttavia, se si vuole avere la possibilità di archiviarli nel controllo del codice sorgente, trascinare i file nella radice della codebase, dove sono visibili.

> [!TIP]
> Per visualizzare i file nascosti in Visual Studio, scegliere il **pulsante Mostra** tutti i file sulla barra Esplora soluzioni barra **degli strumenti.**

## <a name="define-tasks-with-tasksvsjson"></a>Definire le attività con tasks.vs.json

È possibile automatizzare gli script di compilazione o qualsiasi altra operazione esterna per i file inclusi nell'area di lavoro corrente eseguendoli come attività direttamente nell'IDE. Per configurare una nuova attività, è possibile fare clic con il pulsante destro del mouse su un file o una cartella e scegliere **Configura attività**.

![Menu Configura attività](../ide/media/customize-configure-tasks-menu.png)

Viene così creato (o aperto) il file *tasks.vs.json* nella cartella *.vs*. È possibile definire un'attività di compilazione o un'attività arbitraria in questo file, quindi richiamarla usando il nome specificato dal menu di scelta rapida di **Esplora soluzioni**.

Le attività personalizzate possono essere aggiunte a singoli file o a tutti i file di un tipo specifico. Ad esempio, NuGet file di pacchetto possono essere configurati per avere un'attività "Ripristina pacchetti" oppure tutti i file di origine possono essere configurati per avere un'attività di analisi statica, ad esempio un linter per tutti i.js *file.*

### <a name="define-custom-build-tasks"></a>Definire attività di compilazione personalizzate

Se la codebase usa strumenti di compilazione personalizzati che Visual Studio non riconosce, non è possibile eseguire il codice né eseguirne il debug in Visual Studio se non dopo aver completato alcuni passaggi di configurazione. Visual Studio include *attività di compilazione* in cui è possibile indicare a Visual Studio come compilare, ricompilare e pulire il codice. Il *tasks.vs.jsnel* file dell'attività di compilazione Visual Studio ciclo di sviluppo interno agli strumenti di compilazione personalizzati usati dalla codebase.

Si consideri una codebase costituita da un singolo file C# denominato *hello.cs*. Il *makefile per* una codebase di questo tipo potrebbe essere simile al seguente:

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

Per un *makefile di questo tipo* che contiene destinazioni di compilazione, pulizia e *ricompilazione,* è possibile definire letasks.vs.jsnel file. Il file contiene tre attività di compilazione per la compilazione, la ricompilazione e la pulizia della codebase, usando NMAKE come strumento di compilazione.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

Dopo aver definito le attività di compilazione in *tasks.vs.json*, vengono aggiunte altre voci al menu di scelta rapida per i file corrispondenti in **Esplora soluzioni**. Per questo esempio, le opzioni "build", "rebuild" e "clean" vengono aggiunte al menu di scelta rapida di tutti i *file makefile.*

![Menu di scelta rapida per makefile con le opzioni Compila, Ricompila e Pulisci](media/customize-build-rebuild-clean.png)

> [!NOTE]
> I comandi vengono visualizzati nel menu di scelta sotto il comando **Configura attività** a causa delle impostazioni `contextType`. "Compila", "Ricompila" e "Pulisci" sono comandi di compilazione, quindi vengono visualizzati nella sezione della compilazione al centro del menu di scelta rapida.

Quando si seleziona una di queste opzioni, l'attività viene eseguita. L'output viene visualizzato nella **finestra di output** e gli errori di compilazione vengono visualizzati nell'**elenco errori**.

### <a name="define-arbitrary-tasks"></a>Definire attività arbitrarie

È possibile definire attività arbitrarie nel file *tasks.vs.json* file, per eseguire qualsiasi operazione desiderata. Ad esempio, è possibile definire un'attività per visualizzare il nome del file attualmente selezionato nella finestra **Output** o per elencare i file in una directory specificata.

L'esempio seguente illustra *tasks.vs.jsfile* che definisce una singola attività. Quando viene richiamata, l'attività visualizza il nome del file con estensione *.js* attualmente selezionato.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName` specifica il nome visualizzato nel menu di scelta rapida.
- `appliesTo` specifica i file su cui può essere eseguito il comando.
- La proprietà `command` specifica il comando da richiamare. In questo esempio, la variabile di ambiente `COMSPEC` viene usata per identificare l'interprete della riga di comando, in genere *cmd.exe*.
- La proprietà `args` specifica gli argomenti da passare al comando richiamato.
- La macro `${file}` recupera il file selezionato in **Esplora soluzioni**.

Dopo il salvataggio di *tasks.vs.json*, è possibile fare clic con il pulsante destro del mouse su qualsiasi file con estensione *.js* nella cartella e scegliere **Echo filename** (Echo nomefile). Il nome del file viene visualizzato nella finestra **Output**.

> [!NOTE]
> Se la codebase non contiene un file *tasks.vs.json*, è possibile crearne uno scegliendo **Configura attività** dal menu di scelta rapida di un file in **Esplora soluzioni**.

Il prossimo esempio definisce un'attività che elenca i file e le sottocartelle della directory *bin*.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}` è una macro personalizzata definita innanzitutto prima del blocco `tasks`. La macro viene poi chiamata nella proprietà `args`.

Questa attività si applica a tutti i file. Quando si apre il menu di scelta rapida per qualsiasi file in **Esplora soluzioni**, il nome dell'attività **List Outputs** (Elenca output) viene visualizzato nella parte inferiore del menu. Quando si sceglie **List Outputs** (Elenca output) il contenuto della directory *bin* viene elencato nella finestra **Output** in Visual Studio.

![Attività arbitraria nel menu di scelta rapida](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>Ambito settings

Più file *tasks.vs.json* possono essere presenti alla radice e nelle sottodirectory di una codebase. Questa progettazione consente la flessibilità necessaria per ottenere comportamenti diversi nelle varie sottodirectory della codebase. Visual Studio consente di aggregare le impostazioni, o di eseguirne l'override in tutta la codebase, con l'ordine di priorità seguente per i file:

- I file di impostazioni nella cartella *.vs* della cartella radice.
- La directory in cui viene calcolata un'impostazione.
- La directory padre della directory corrente, risalendo fino alla directory radice.
- I file di impostazioni nella directory radice.

Queste regole di aggregazione si applicano a *tasks.vs.json*. Per informazioni su come vengono aggregate le impostazioni in altri file, vedere la sezione corrispondente in questo articolo.

### <a name="properties-for-tasksvsjson"></a>Proprietà per tasks.vs.json

Questa sezione descrive alcune delle proprietà che è possibile specificare in *tasks.vs.json*.

#### <a name="appliesto"></a>appliesTo

È possibile creare attività per qualsiasi file o cartella specificandone il nome nel campo `appliesTo`, ad esempio `"appliesTo": "hello.js"`. È possibile usare le maschere di file seguenti come valori:

|Maschera di file|Descrizione|
|-|-|
|`"*"`| L'attività è disponibile per tutti i file e le cartelle nell'area di lavoro|
|`"*/"`| L'attività è disponibile per tutte le cartelle nell'area di lavoro|
|`"*.js"`| l'attività è disponibile per tutti i file con estensione *.js* nell'area di lavoro|
|`"/*.js"`| l'attività è disponibile per tutti i file con estensione *.js* nella radice dell'area di lavoro|
|`"src/*/"`| l'attività è disponibile per tutte le sottocartelle della *cartella src*|
|`"makefile"`| L'attività è disponibile per tutti i file *makefile* nell'area di lavoro|
|`"/makefile"`| l'attività è disponibile solo per *il makefile* nella radice dell'area di lavoro|

#### <a name="macros-for-tasksvsjson"></a>Macro per tasks.vs.json

|Macro|Descrizione|
|-|-|
|`${env.<VARIABLE>}`| Specifica qualsiasi variabile di ambiente (ad esempio, ${env.PATH}, ${env.COMSPEC} e così via) impostata per il prompt dei comandi per gli sviluppatori. Per altre informazioni, vedere [Prompt dei comandi per gli sviluppatori e PowerShell per sviluppatori.](../ide/reference/command-prompt-powershell.md)|
|`${workspaceRoot}`| Percorso completo della cartella dell'area di lavoro, ad esempio *C:\sources\hello*|
|`${file}`| Percorso completo del file o della cartella selezionata per eseguire questa attività, ad esempio *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| Percorso relativo del file o della cartella ( ad esempio, *src\hello.js*)|
|`${fileBasename}`| Nome del file senza percorso o estensione ( ad esempio, *hello*)|
|`${fileDirname}`| Percorso completo del file, escluso il nome file ( ad *esempio, C:\sources\hello\src*)|
|`${fileExtname}`| Estensione del file selezionato, ad esempio.js *)*|

## <a name="configure-debugging-with-launchvsjson"></a>Configurare il debug con launch.vs.json

Per configurare i progetti CMake per il debug, vedere [Configurare le sessioni di debug CMake](/cpp/build/configure-cmake-debugging-sessions).

1. Per configurare la codebase per il debug, in **Esplora soluzioni** scegliere il comando **Impostazioni per debug e avvio** dal menu di scelta rapida del file eseguibile.

   ![Menu di scelta rapida Impostazioni per debug e avvio](media/customize-debug-launch-menu.png)

1. Nela finestra di dialogo **Seleziona un debugger** scegliere un'opzione e quindi scegliere il pulsante **Seleziona**.

   ![Finestra di dialogo Seleziona un debugger](media/customize-select-a-debugger.png)

   Se il file *launch.vs.json* non esiste già, viene creato.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. Fare quindi clic con il pulsante destro del mouse sul file eseguibile in **Esplora soluzioni** e scegliere **Imposta come elemento di avvio**.

   Il file eseguibile viene designato come elemento di avvio per la codebase e il titolo del pulsante di debug **Avvia** cambia in base al nome dell'eseguibile.

   ![Pulsante Avvia personalizzato](media/customize-start-button.png)

   Quando si sceglie **F5**, il debugger viene avviato e si interrompe in corrispondenza di qualsiasi punto di interruzione già impostato. Tutte le finestre di debug già note sono disponibili e funzionanti.

   > [!IMPORTANT]
   > Per altri dettagli sulle attività di compilazione e debug personalizzate nei progetti di cartelle aperte C++, vedere Supporto open folder per sistemi di compilazione [C++ in Visual Studio](/cpp/build/open-folder-projects-cpp).

### <a name="specify-arguments-for-debugging"></a>Specificare gli argomenti per il debug

È possibile specificare argomenti della riga di comando da passare per il debug nel file *launch.vs.json*. Aggiungere gli argomenti nella matrice `args`, come illustrato nell'esempio seguente:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

Quando si salva questo file, il nome della nuova configurazione viene visualizzato nell'elenco a discesa delle destinazioni di debug ed è possibile selezionarlo per avviare il debugger. È possibile creare il numero desiderato di configurazioni di debug.

![Elenco a discesa delle configurazioni di debug](media/customize-debug-configurations.png)

> [!NOTE]
> La proprietà array inlaunch.vs.jsviene letta da due percorsi di file la directory radice per `configurations`  la &mdash; codebase e la directory con estensione *vs.* In caso di conflitto viene data priorità al valore in *.vs\launch.vs.json*.

## <a name="additional-settings-files"></a>File di impostazioni aggiuntivi

Oltre ai tre file *json* descritti in questo argomento, Visual Studio legge anche le impostazioni da alcuni file aggiuntivi, se esistenti nella codebase.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio legge un certo numero di impostazioni da un file denominato *settings.json*, se si trova in una directory denominata *.vscode*. Questa funzionalità è disponibile per le codebase sviluppate in precedenza in Visual Studio Code. Attualmente, l'unica impostazione letta da *.vscode\settings.json* è `files.exclude`, che consente di filtrare visivamente file in Esplora soluzioni e da alcuni strumenti di ricerca.

La codebase può includere qualsiasi numero di file *.vscode\settings.json*. Le impostazioni lette da questo file vengono applicate alla directory padre di *.vscode* e a tutte le relative sottodirectory.

### <a name="gitignore"></a>gitignore

I file con estensione *gitignore* vengono usati per indicare a Git quali file ignorare, ovvero, i file e le directory che non si vogliono archiviare. I file con estensione *gitignore* vengono in genere inclusi come parte di una codebase, in modo che le impostazioni possano essere condivise con tutti gli sviluppatori della codebase. Visual Studio legge i modelli nei file con estensione *gitignore* per filtrare gli elementi visivamente e da alcuni strumenti di ricerca.

Le impostazioni lette dal file con estensione *gitignore* vengono applicate alla directory padre e a tutte le sottodirectory.

## <a name="see-also"></a>Vedi anche

- [Sviluppare codice senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Progetti Apri cartella per C++](/cpp/build/open-folder-projects-cpp)
- [Progetti CMake per C++](/cpp/build/cmake-projects-in-visual-studio)
- [Riferimenti a NMAKE](/cpp/build/reference/nmake-reference)
- [Funzionalità dell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)
