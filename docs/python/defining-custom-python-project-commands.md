---
title: Definire comandi di menu personalizzati per i progetti Python
description: Modificando i file di progetto e delle destinazioni è possibile aggiungere comandi personalizzati al menu di scelta rapida del progetto Python in Visual Studio per richiamare programmi eseguibili, script, moduli, frammenti di codice inline e pip.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 63679d590e341cce8f5ee76d4b359821b3f213b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628325"
---
# <a name="define-custom-commands-for-python-projects"></a>Definire comandi personalizzati per i progetti Python

Mentre si lavora ai progetti Python è possibile che risulti necessario passare a una finestra di comando per eseguire script o moduli specifici, comandi pip o altri strumenti arbitrari. Per migliorare il flusso di lavoro, è possibile aggiungere comandi personalizzati al sottomenu **Python** nel menu di scelta rapida per i progetti Python. Tali comandi possono essere eseguiti in una finestra della console o nella finestra **Output** di Visual Studio. È anche possibile usare espressioni regolari per indicare a Visual Studio come analizzare gli errori e gli avvisi dall'output del comando.

Per impostazione predefinita, il menu contiene solo il comando **Esegui PyLint**:

![Aspetto predefinito del sottomenu Python nel menu di scelta rapida di un progetto](media/custom-commands-default-menu.png)

I comandi personalizzati vengono visualizzati in questo stesso menu di scelta rapida. I comandi personalizzati vengono aggiunti a un file di progetto direttamente e sono applicabili a tale singolo progetto. È anche possibile definire i comandi personalizzati in un file con estensione *targets* che può essere facilmente importato in più file di progetto.

Alcuni modelli di progetto Python in Visual Studio aggiungono già comandi personalizzati tramite il relativo file con estensione *targets*. Ad esempio, i modelli Progetto Web Bottle e Progetto Web Flask aggiungono entrambi due comandi, **Avvia il server** e **Avvia il server di debug**. Il modello Progetto Web Django aggiunge alcuni altri comandi oltre a questi:

![Aspetto del sottomenu Python nel menu di scelta rapida di un progetto Django](media/custom-commands-django-menu.png)

Ogni comando personalizzato può fare riferimento a un file di Python, un modulo di Python, codice Python inline, un eseguibile arbitrario o un comando pip. È anche possibile specificare come e dove viene eseguito il comando.

> [!Tip]
> Ogni volta che si apportano modifiche a un file di progetto in un editor di testo, è necessario ricaricare il progetto in Visual Studio per applicare tali modifiche. Ad esempio, è necessario ricaricare un progetto dopo l'aggiunta di definizioni di comandi personalizzati, per visualizzarli nel menu di scelta rapida del progetto.
>
> Come è probabilmente noto, Visual Studio fornisce un mezzo per modificare direttamente il file di progetto. Fare prima clic con il pulsante destro del mouse sul file **\<project-name>** di progetto e scegliere Scarica progetto **,** quindi fare di nuovo clic con il pulsante destro del mouse e scegliere Modifica per aprire il progetto nell'editor Visual Studio progetto. È quindi possibile apportare modifiche e salvarle, fare clic con il pulsante destro del mouse sul progetto ancora una volta e scegliere **Ricarica progetto**. Viene anche richiesto di confermare la chiusura del file di progetto nell'editor.
>
> Durante lo sviluppo di un comando personalizzato, tuttavia, tutti questi clic possono risultare noiosi. Per un flusso di lavoro più efficiente, caricare il progetto in Visual Studio e aprire anche il file con estensione *.yproj* in un editor separato, ad esempio in un'altra istanza di Visual Studio, in Visual Studio Code, nel Blocco note e così via. Quando si salvano le modifiche nell'editor e si passa a Visual Studio, Visual Studio rileva le modifiche e chiede se ricaricare il progetto ( il progetto è stato modificato all'esterno **\<name> dell'ambiente).** Selezionare **Ricarica** e le modifiche vengono applicate immediatamente in un unico passaggio.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>Procedura dettagliata: Aggiungere un comando a un file di progetto

Per acquisire familiarità con i comandi personalizzati, in questa sezione viene illustrato un semplice esempio che esegue il file di avvio di un progetto direttamente usando *python.exe*. Tale comando è in effetti uguale all'uso di **Debug**  >  **Avvia senza eseguire il debug.**

1. Creare un nuovo progetto denominato "Python-CustomCommands" usando il modello **Applicazione Python**. (Se non si conosce già la procedura, vedere [Guida rapida: creare un progetto Python da un modello](quickstart-02-python-in-visual-studio-project-from-template.md) per istruzioni.)

1. In *Python_CustomCommands.py*, aggiungere il codice `print("Hello custom commands")`.

1. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni**, scegliere **Python** e notare che l'unico comando visualizzato nel sottomenu è **Esegui PyLint**. I comandi personalizzati vengono visualizzati in questo stesso sottomenu.

1. Come indicato nell'introduzione, aprire *Python-CustomCommands.pyproj* in un editor di testo separato. Aggiungere quindi le righe seguenti alla fine del file all'interno del tag `</Project>` di chiusura e salvare il file.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Tornare a Visual Studio e selezionare **Ricarica** quando viene richiesto come procedere in seguito alla modifica del file. Controllare quindi di nuovo il menu **Python** per vedere che **Esegui PyLint** è ancora è l'unico elemento visualizzato perché le righe aggiunte replicano solo il gruppo di proprietà `<PythonCommands>` predefinito contenente il comando PyLint.

1. Passare all'editor con il file di progetto e aggiungere la definizione `<Target>` seguente dopo `<PropertyGroup>`. Come descritto più avanti in questo articolo, questo elemento `Target` definisce un comando personalizzato per eseguire il file di avvio (identificato dalla proprietà "StartupFile") usando *python.exe* in una finestra della console. L'attributo `ExecuteIn="consolepause"` usa una console che attende che l'utente prema un tasto prima della chiusura.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. Aggiungere il valore dell'attributo `Name` della destinazione al gruppo di proprietà `<PythonCommands>` aggiunto in precedenza, in modo che l'elemento sia simile al codice riportato di seguito. L'aggiunta del nome della destinazione a questo elenco è l'operazione che consente di aggiungerla al menu **Python**.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    Se si vuole che il comando venga visualizzato prima di quelli definiti in `$(PythonCommands)`, posizionarlo prima di tale token.

1. Salvare il file di progetto, passare a Visual Studio e ricaricare il progetto quando viene richiesto. Fare quindi clic con il pulsante destro del mouse sul progetto **Python CustomCommands** e scegliere **Python**. Nel menu dovrebbe essere visualizzato il comando **Run startup file**. Se non viene visualizzata la voce di menu, controllare di avere aggiunto il nome all'elemento `<PythonCommands>`. Vedere anche [Risoluzione dei problemi](#troubleshooting) più avanti in questo articolo.

    ![Comando personalizzato visualizzato nel menu di scelta rapida di Python](media/custom-commands-walkthrough-menu-item.png)

1. Selezionare il comando **Run startup file**. Dovrebbe essere visualizzata una finestra di comando con il testo **Hello custom commands** seguito da **Premere un tasto per continuare**.  Premere un tasto per chiudere la finestra.

    ![Output del comando personalizzato in una finestra della console](media/custom-commands-walkthrough-console.png)

1. Tornare all'editor con il file di progetto e modificare il valore dell'attributo `ExecuteIn` in `output`. Salvare il file, passare a Visual Studio, ricaricare il progetto e richiamare di nuovo il comando. Questa volta l'output del programma viene visualizzato nella finestra **Output** di Visual Studio:

    ![Output del comando personalizzato nella finestra di output](media/custom-commands-walkthrough-output-window.png)

1. Per aggiungere altri comandi, definire un elemento `<Target>` appropriato per ogni comando, aggiungere il nome della destinazione nel gruppo di proprietà `<PythonCommands>` e ricaricare il progetto in Visual Studio.

>[!Tip]
> Se si richiama un comando che usa le proprietà di progetto, ad esempio `($StartupFile)`, e il comando non riesce perché il token non è definito, Visual Studio disabilita il comando fino a quando non si ricarica il progetto. Apportare modifiche al progetto con cui verrebbe definita la proprietà, tuttavia, non aggiorna lo stato di questi comandi, quindi è comunque necessario ricaricare il progetto in questi casi.

## <a name="command-target-structure"></a>Struttura di destinazione del comando

Il formato generale dell'elemento `<Target>` è indicato nel pseudo-codice seguente:

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

Per fare riferimento alle proprietà o alle variabili di ambiente del progetto nei valori di attributo, usare il nome all'interno di un token `$()`, ad esempio `$(StartupFile)` e `$(MSBuildProjectDirectory)`. Per altre informazioni, vedere MSBuild [proprietà .](../msbuild/msbuild-properties.md)

### <a name="target-attributes"></a>Attributi Target

| Attributo | Obbligatorio | Descrizione |
| --- | --- | --- |
| Nome | Sì | Identificatore per il comando all'interno del progetto di Visual Studio. Questo nome deve essere aggiunto al gruppo di proprietà `<PythonCommands>` per visualizzare il comando nel sottomenu Python. |
| Label | Sì | Nome visualizzato dell'interfaccia utente visualizzato nel sottomenu Python. |
| Restituisce | Sì | Deve contenere `@(Commands)`, che identifica la destinazione come comando. |

### <a name="createpythoncommanditem-attributes"></a>Attributi CreatePythonCommandItem

Per tutti i valori di attributo non viene fatta distinzione tra maiuscole e minuscole.

| Attributo | Obbligatorio | Descrizione |
| --- | --- | --- |
| TargetType | Sì | Specifica il contenuto dell'attributo Target e come viene usato insieme all'attributo Arguments:<ul><li>**executable**: eseguire il file eseguibile denominato in Target, aggiungendo il valore in Arguments, come in caso di immissione diretta nella riga di comando. Il valore deve contenere solo un nome di programma senza argomenti.</li><li>**script**: eseguire *python.exe* con il nome di file in Target seguito dal valore in Arguments.</li><li>**module**: eseguire `python -m` seguito dal nome del modulo in Target seguito dal valore in Arguments.</li><li>**code**: eseguire il codice inline contenuto in Target. Il valore di Arguments viene ignorato.</li><li>**pip**: eseguire `pip` con il comando in Target seguito da Arguments. Se ExecuteIn è impostato su "output", tuttavia, pip presuppone il comando `install` e usa Target come nome del pacchetto.</li></ul> |
| Destinazione | Sì | Nome del file, nome del modulo, codice o comando pip da usare, a seconda di TargetType. |
| Argomenti | Facoltativo | Specifica una stringa di argomenti (se presenti) da assegnare alla destinazione. Si noti che quando TargetType è `script`, gli argomenti vengono passati al programma Python e non a *python.exe*. Ignorato per TargetType `code`. |
| ExecuteIn | Sì | Specifica l'ambiente in cui eseguire il comando:<ul><li>**console**: (impostazione predefinita) esegue Target e gli argomenti come se fossero immessi direttamente nella riga di comando. Viene visualizzata una finestra di comando durante l'esecuzione di Target, quindi viene chiusa automaticamente.</li><li>**consolepause**: come console, ma attende una pressione di tasto prima di chiudere la finestra.</li><li>**output**: esegue Target e visualizza i risultati nella finestra di **Output** in Visual Studio. Se TargetType è "pip", Visual Studio usa Target come nome del pacchetto e aggiunge Arguments.</li><li>**repl**: esegue Target nella [finestra interattiva di Python](python-interactive-repl-in-visual-studio.md). Il nome visualizzato facoltativo viene usato per il titolo della finestra.</li><li>**none**: stesso comportamento di console.</li></ul>|
| WorkingDirectory | Facoltativo | Cartella in cui eseguire il comando. |
| ErrorRegex<br>WarningRegEx | Facoltativo | Usato solo quando è ExecuteIn è `output`. Entrambi i valori specificano un'espressione regolare con cui Visual Studio analizza l'output del comando per visualizzare errori e avvisi nella relativa finestra **Elenco errori**. Se non specificato, il comando non influisce sulla finestra **Elenco errori**. Per altre informazioni su cosa prevede Visual Studio , vedere [Gruppi Capture denominati](#named-capture-groups-for-regular-expressions). |
| RequiredPackages | Facoltativo | Elenco di requisiti del pacchetto per il comando con lo stesso formato di [*requirements.txt*](https://pip.pypa.io/en/stable/user_guide/#requirements-files) (pip.readthedocs.io). Il comando **Esegui PyLint**, ad esempio, specifica `pylint>=1.0.0`. Prima di eseguire il comando, Visual Studio verifica che siano installati tutti i pacchetti nell'elenco. Visual Studio usa pip per installare tutti i pacchetti mancanti. |
| Ambiente | Facoltativo | Stringa di variabili di ambiente da definire prima di eseguire il comando. Ogni variabile usa il formato \<NAME> = \<VALUE> con più variabili separate da punto e virgola. Una variabile con più valori deve essere racchiusa tra virgolette singole o doppie, come in 'NOME=VALORE1;VALORE2'. |

#### <a name="named-capture-groups-for-regular-expressions"></a>Gruppi Capture denominati per le espressioni regolari

Durante l'analisi di errori e avvisi nell'output di un comando, Visual Studio presuppone che le espressioni regolari nei valori `ErrorRegex` e `WarningRegex` usino i gruppi denominati seguenti:

- `(?<message>...)`: testo dell'errore
- `(?<code>...)`: codice di errore
- `(?<filename>...)`: nome del file per cui viene segnalato l'errore
- `(?<line>...)`: numero di riga della posizione nel file per cui viene segnalato l'errore
- `(?<column>...)`: numero di colonna della posizione nel file per cui viene segnalato l'errore

Ad esempio, PyLint produce avvisi nel formato seguente:

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Per consentire a Visual Studio di estrarre le informazioni appropriate da tali avvisi e visualizzarle nella finestra **Elenco errori**, il valore `WarningRegex` per il comando **Esegui Pylint** è il seguente:

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(Si noti che `msg_id` nel valore deve essere effettivamente `code`, vedere [Problema 3680](https://github.com/Microsoft/PTVS/issues/3680).)

## <a name="create-a-targets-file-with-custom-commands"></a>Creare un file con estensione targets con comandi personalizzati

Definire i comandi personalizzati in un file di progetto li rende disponibili solo per tale file di progetto. Per usare i comandi in più file di progetto, è invece necessario definire il gruppo di proprietà `<PythonCommands>` e tutti gli elementi `<Target>` in un file con estensione *targets*. È quindi possibile importare tale file in singoli file di progetto.

Il file con estensione *targets* è formattato come segue:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

Per caricare un file con estensione *targets* in un progetto, inserire un elemento `<Import Project="(path)">` in qualsiasi posizione all'interno dell'elemento `<Project>`. Ad esempio, se è disponibile un file denominato *CustomCommands.targets* in una sottocartella *targets* nel progetto, usare il codice seguente:

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> Ogni volta che si modifica il file con estensione *targets*, è necessario ricaricare la *soluzione* che contiene un progetto e non solo il progetto stesso.

## <a name="example-commands"></a>Comandi di esempio

### <a name="run-pylint-module-target"></a>Eseguire PyLint (destinazione modulo)

Il codice seguente viene visualizzato nel file *Microsoft.PythonTools.targets*:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>Eseguire l'installazione pip con un pacchetto specifico (destinazione pip)

Il comando seguente esegue `pip install my-package` nella finestra di **output**. È possibile usare tale comando durante lo sviluppo di un pacchetto e il test dell'installazione. Si noti che Target contiene il nome del pacchetto invece del comando `install`, implicito quando si usa `ExecuteIn="output"`.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>Visualizzare i pacchetti pip non aggiornati (destinazione pip)

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>Eseguire un eseguibile con consolepause

Il comando seguente esegue semplicemente `where` per visualizzare i file di Python nella cartella del progetto:

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>Comandi Avvia il server e Avvia il server di debug

Per esaminare la definizione dei comandi **Avvia il server** e **Avvia il server di debug** per i progetti Web, esaminare [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets) (GitHub).

### <a name="install-package-for-development"></a>Installare il pacchetto per lo sviluppo

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Da [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usato con l'autorizzazione .*

### <a name="generate-windows-installer"></a>Generare un programma di installazione Windows

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*Da [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usato con l'autorizzazione .*

### <a name="generate-wheel-package"></a>Generare un pacchetto wheel

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*Da [fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa) (GitHub), usato con l'autorizzazione .*

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="message-the-project-file-could-not-be-loaded"></a>Messaggio: "Impossibile caricare il file di progetto"

Indica la presenza di errori di sintassi nel file di progetto. Il messaggio include l'errore specifico con un numero di riga e la posizione di carattere.

### <a name="console-window-closes-immediately-after-command-is-run"></a>La finestra della console viene chiusa immediatamente dopo l'esecuzione del comando

Usare `ExecuteIn="consolepause"` invece di `ExecuteIn="console"`.

### <a name="command-does-not-appear-on-the-menu"></a>Il comando non viene visualizzato nel menu

Verificare che il comando sia incluso nel gruppo di proprietà `<PythonCommands>` e che il nome nell'elenco di comandi corrisponda al nome specificato nell'elemento `<Target>`.

Negli elementi seguenti, ad esempio, il nome "Example" nel gruppo di proprietà non corrisponde al nome "ExampleCommand" nella destinazione. Visual Studio non trova un comando denominato "Example" quindi non viene visualizzato alcun comando. Usare "ExampleCommand" nell'elenco dei comandi o modificare il nome della destinazione in "Example".

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>Messaggio: "Si è verificato un errore durante l'esecuzione di \<command name> . Impossibile ottenere il comando \<target-name> dal progetto."

Indica che il contenuto degli elementi `<Target>` o `<CreatePythonCommandItem>` non è corretto. Le possibili cause includono:

- L'attributo `Target` obbligatorio è vuoto.
- L'attributo `TargetType` obbligatorio è vuoto o contiene un valore non riconosciuto.
- L'attributo `ExecuteIn` obbligatorio è vuoto o contiene un valore non riconosciuto.
- L'attributo `ErrorRegex` o `WarningRegex` viene specificato senza impostare `ExecuteIn="output"`.
- Gli attributi non riconosciuti esistono nell'elemento. Ad esempio, è possibile che sia stato digitato erroneamente `Argumnets` invece di `Arguments`.

I valori di attributo possono essere vuoti se si fa riferimento a una proprietà non definita. Ad esempio, se si usa il token `$(StartupFile)` ma nel progetto non è stato definito alcun file di avvio, il token viene risolto in una stringa vuota. In questi casi, può essere utile definire un valore predefinito. Ad esempio, l'impostazione predefinita dei comandi **Avvia il server** e **Avvia il debug del server** definiti nei modelli di progetto Bottle, Flask e Django è *manage.py* se non è stato specificato un file di avvio del server in altro modo nelle proprietà del progetto.

### <a name="visual-studio-stops-responding-and-crashes-when-running-the-command"></a>Visual Studio smette di rispondere e si arresta in modo anomalo quando si esegue il comando

Probabilmente si sta tentando di eseguire un comando della console con `ExecuteIn="output"`, nel qual caso potrebbe verificarsi un arresto anomalo di Visual Studio durante il tentativo di analizzare l'output. In alternativa, utilizzare `ExecuteIn="console"`. (Vedere [Problema 3682](https://github.com/Microsoft/PTVS/issues/3681).)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Il comando eseguibile "non è riconosciuto come comando interno o esterno, un programma eseguibile o un file batch"

Quando si usa `TargetType="executable"`, il valore in `Target` deve essere *solo* il nome del programma senza argomenti, ad esempio solo *python* o *python.exe*. Spostare gli eventuali argomenti nell'attributo `Arguments`.
