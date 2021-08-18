---
title: Eseguire l'aggiornamento da Dotfuscator Community 5
ms.date: 07/21/2021
ms.devlang: dotnet
ms.topic: how-to
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, edizione community, offuscamento, .NET, gratis, Visual Studio 2019, Visual Studio 2017, Visual Studio, aggiornare, riga di comando
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Informazioni su come aggiornare la copia gratuita di Dotfuscator Community 5 inclusa in Visual Studio.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: c1a6375a26325ca6f297b78a3024117e6e39132f
ms.sourcegitcommit: f930bc28bdb0ba01d6f7cb48f229afecfa0c90cd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2021
ms.locfileid: "122334922"
---
# <a name="upgrade-from-dotfuscator-community-5"></a>Eseguire l'aggiornamento da Dotfuscator Community 5

Informazioni su come eseguire l'aggiornamento a PreEmptive Protection - Dotfuscator Community 6.

A seconda della cronologia di installazione e della versione di Visual Studio, è possibile che sia in esecuzione Dotfuscator Community 5, la versione principale precedente. In tal caso, è consigliabile eseguire l'aggiornamento, perché è importante assicurarsi che al codice vengano fornite le [misure di protezione più recenti.][always-improving] Gli aggiornamenti sono disponibili gratuitamente.

Questo articolo illustra come determinare la versione corrente, come eseguire l'aggiornamento alla versione 6, se necessario, e quali funzionalità sono state sostituite o rimosse tra le due versioni.

## <a name="determine-the-dotfuscator-version"></a>Determinare la versione di Dotfuscator

Se non si è certi della versione di Dotfuscator in esecuzione, è possibile determinare la versione eseguendo una delle opzioni seguenti:

* Avviare l'interfaccia utente grafica [(GUI)][gui] di Dotfuscator Community scegliendo Strumenti dal **menu** Strumenti di Visual Studio e selezionando **PreEmptive Protection - Dotfuscator Community**.

  Nell'interfaccia utente grafica di Dotfuscator aprire il menu **?** e selezionare **Informazioni su...** per visualizzare la schermata Informazioni.
  
  Questa schermata elenca la versione di Dotfuscator.

* Se Dotfuscator è integrato nella compilazione con l'interfaccia della riga di comando [,ad][cli] esempio con le app [Xamarin,][xamarin] è anche possibile controllare i log di compilazione per una riga simile all'esempio seguente:

  ```no-highlight
  Dotfuscator Community Version 5.42.0.9514-e0e25f754
  ```

  Potrebbe essere necessario aumentare il livello di dettaglio della compilazione per visualizzare questo testo.
  Per Visual Studio, vedere [Verbosity Impostazioni][verbosity].

Il primo numero intero della versione, prima del primo punto, indica la versione principale di `.` Dotfuscator. Se il primo numero intero è , è necessario eseguire i passaggi di aggiornamento in questa pagina, in modo da poter sfruttare le funzionalità e gli aggiornamenti di protezione più recenti di `5` Dotfuscator 6.

## <a name="upgrade-instructions"></a>Istruzioni per l'aggiornamento

Questa sezione include set di istruzioni per l'aggiornamento degli utilizzi tipici di Dotfuscator Community dalla versione 5 alla versione 6.

### <a name="install-dotfuscator-6"></a>Installare Dotfuscator 6

Dotfuscator Community viene distribuito come estensione per Visual Studio. Le istruzioni per installare Dotfuscator 6 variano in base alla versione Visual Studio disponibile:

* **Visual Studio 2019** Dotfuscator Community 6 è incluso nelle versioni successive di Visual Studio 2019 (versione 16.10.0 e successive).
  [Aggiornare Visual Studio 2019 alla][vs-update] versione più recente. L'Visual Studio aggiorna automaticamente qualsiasi installazione di Dotfuscator Community 5 a Dotfuscator Community 6.

    * Se Dotfuscator non è già installato, aggiornare prima Visual Studio e quindi vedere [Installazione][install].

    * Oltre alle versioni con Visual Studio, è sempre possibile ottenere le versioni più recenti di Dotfuscator Community dalla pagina [di download di Dotfuscator.][download]

* **Visual Studio 2017** Questa versione di Visual Studio fornita solo con Dotfuscator Community 5.
  Tuttavia, è possibile installare o eseguire l'aggiornamento a Dotfuscator Community 6 dalla pagina Download di [Dotfuscator][download] e selezionando il collegamento di download appropriato.

  Eseguire il `.vsix` file scaricato e seguire le istruzioni per installare Dotfuscator Community 6 in Visual Studio. Verranno aggiornate anche le Community dotfuscator esistenti Community 5.

* **Versioni precedenti di Visual Studio** Dotfuscator Community 6 non è supportato in queste versioni di Visual Studio.
  È consigliabile eseguire l'aggiornamento a una versione più recente di Visual Studio o da [Dotfuscator Community a Dotfuscator Professional][pro].

Se in [][register] precedenza era stato registrato Dotfuscator Community 5, tale registrazione verrà convertita automaticamente la prima volta che si esegue Dotfuscator Community 6.

<a name="steps-cli"></a>

### <a name="update-paths-to-the-cli"></a>Aggiornare i percorsi all'interfaccia della riga di comando

Se in precedenza è stata usata l'interfaccia della riga di comando [di][cli] Dotfuscator 5 per proteggere l'app, sarà necessario aggiornare il percorso dell'interfaccia della riga di comando in tutti i progetti e compilare script che vi fanno riferimento. Include progetti che usano Dotfuscator [Community'integrazione Xamarin di Dotfuscator.][xamarin]

Il motivo per cui un percorso all'interfaccia della riga di comando di Dotfuscator potrebbe ora non essere valido è perché i nomi di alcuni dei file eseguibili installati con Dotfuscator Community sono stati modificati in Dotfuscator 6. Questa modifica rende gli stessi nomi di file eseguibili in Dotfuscator Community e Dotfuscator Professional.

| Eseguibile per...                     | Dotfuscator 5         | Dotfuscator 6         |
|---------------------------------------|-----------------------|-----------------------|
| [Interfaccia utente grafica][gui] | `dotfuscator.exe`     | `dotfuscatorUI.exe`   |
| [CLI][cli]   | `dotfuscatorCLI.exe`  | `dotfuscator.exe`     |

> [!NOTE]
> Il percorso dell'interfaccia della riga di comando potrebbe non essere valido anche se si esegue l'aggiornamento tra le versioni principali di Visual Studio o si passa a un'edizione Visual Studio, perché l'interfaccia della riga di comando di Dotfuscator viene installata nella directory di installazione di Visual Studio.
Anche i sintomi e la soluzione elencati di seguito si applicano a questo scenario.

Se la compilazione usa un percorso dell'interfaccia della riga di comando di Dotfuscator non valido, è possibile che si verificano errori come uno degli esempi seguenti:

`'"[...]\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe"' is not recognized as an internal or external command,
operable program or batch file.`

`The command ""[...]\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe" Dotfuscator.xml" exited with code 9009.`

`When the DotfuscatorXamarinEnabled property is 'true', the Dotfuscator command line interface specified by
DotfuscatorXamarinCliPath ('[...]\DotfuscatorCE\dotfuscatorCLI.exe') must exist.`

Per aggiornare la compilazione in modo da usare il percorso corretto dell'interfaccia della riga di comando:

1. Avviare l'interfaccia utente grafica [][gui] Community Dotfuscator scegliendo Visual Studio's **Tools** (Strumenti) e selezionando **PreEmptive Protection - Dotfuscator Community**.
   
2. Nell'interfaccia utente grafica Community Dotfuscator passare al **menu** Strumenti e selezionare Prompt dei comandi **di Dotfuscator**.

3. Nel prompt dei comandi visualizzato digitare `where dotfuscator.exe` .
   Copiare il primo percorso visualizzato in un documento di testo normale per riferimento successivo. Questo percorso è il nuovo percorso di Dotfuscator Community'interfaccia della riga di comando di 6.

4. Aprire la configurazione del progetto o della compilazione in base alle esigenze del sistema di compilazione.

    * Per Visual Studio, è necessario aprire il file di progetto ( `.csproj` , o ) come testo `.vbproj` `.fsproj` normale. [Aprire un file di progetto](../solutions-and-projects-in-visual-studio.md#project-file) in Visual Studio.
    
    * Se in precedenza è stata usata l'integrazione [Xamarin][xamarin] di Dotfuscator Community per proteggere un'app Xamarin, ricordare che Dotfuscator è integrato in ogni singolo progetto di app (ad esempio e ) separatamente e non nei progetti di libreria `MyProject.Android.csproj` `MyProject.iOS.csproj` condivisa.
      È necessario aggiornare tutti i progetti di app che attualmente usano Dotfuscator.

5. Individuare le posizioni all'interno del progetto o della configurazione di compilazione in cui viene usato un percorso precedente di Dotfuscator Community'interfaccia della riga di comando di 5.
   In genere è un percorso che termina con `dotfuscatorCLI.exe` .

    * Quando si aggiorna un progetto usando Dotfuscator Community'integrazione [Xamarin][xamarin] di Dotfuscator, il percorso precedente si trova tra i `<DotfuscatorXamarinCliPath>` tag e `</DotfuscatorXamarinCliPath>` .

6. Sostituire i percorsi vecchi che si trovano nel passaggio 5 con il nuovo percorso specificato nel passaggio 3.
   
   Se uno dei percorsi meno vecchi non è un percorso assoluto, è necessario modificare il nuovo percorso in modo appropriato in base al contesto.
   Nell'esempio seguente la variabile di ambiente è stata usata nel percorso precedente, quindi anche il nuovo percorso corrispondente deve `VSInstallDir` eseguire questa operazione.

    * Nuovo percorso del passaggio 3: `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscator.exe`
    * Percorso precedente nel file di progetto: `%VSInstallDir%\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscatorCLI.exe`
    * Nuovo percorso nel file di progetto: `%VSInstallDir%\Common7\IDE\Extensions\PreEmptiveSolutions\DotfuscatorCE\dotfuscator.exe`

7. Se si usa un sistema di controllo del codice sorgente, ad esempio Git, assicurarsi che le modifiche del passaggio 6 siano riflesse in tale sistema.
   Distribuire queste modifiche al resto del team in base alle esigenze del sistema e dell'organizzazione.

> [!WARNING]
> Poiché fa riferimento all'interfaccia utente grafica (GUI) in Dotfuscator 5, ma fa riferimento all'interfaccia della riga di comando `dotfuscator.exe` in Dotfuscator 6, prestare attenzione quando si aggiornano gli script di compilazione condivisi tra più computer.
>
> In un computer in cui è installato Dotfuscator 5 che esegue uno script aggiornato per Dotfuscator 6, lo script avvierà l'interfaccia utente grafica anziché l'interfaccia della riga di comando prevista. **Ciò potrebbe causare l'esito positivo della compilazione nonostante non sia stata applicata la protezione di Dotfuscator, vale a dire che i pacchetti di output NON saranno protetti.**
>
> In altri casi, potrebbe invece causare un errore di compilazione.
>
> Per evitare questi scenari, aggiornare Dotfuscator Community dalla versione 5 alla versione 6 in tutti i computer e compilare gli script contemporaneamente.

<a name="steps-config-files"></a>

### <a name="upgrade-dotfuscator-config-files"></a>Aggiornare i file di configurazione di Dotfuscator

*Tutti* I file di configurazione di Dotfuscator (ad esempio ) creati prima di `Dotfuscator.xml` Dotfuscator 6 dovranno essere aggiornati.

Se si tenta di eseguire l'interfaccia della riga di comando di Dotfuscator con un file di configurazione precedente, si otterranno errori come gli esempi seguenti:

`Dotfuscator Engine Initialization error: PreEmptive Analytics, Authenticode signing, and the Introduce Explicit Method Overrides
setting are no longer supported. Please open your Dotfuscator config in the Config Editor which will automatically upgrade it.`

> [!IMPORTANT]
> Questo errore verrà visualizzato e sarà necessario aggiornare il file di configurazione anche se non si usavano le funzionalità indicate.

Per aggiornare un file di configurazione:

1. Avviare l'interfaccia utente grafica [(GUI)][gui] di Dotfuscator Community scegliendo Strumenti dal **menu** Strumenti di Visual Studio e selezionando **PreEmptive Protection - Dotfuscator Community**.

2. Aprire il file di configurazione dotfuscator in questione (CTRL+O).

3. Nella scheda Output di compilazione verrà visualizzato *il messaggio* seguente:

    `PreEmptive Analytics, Authenticode signing, and the Introduce Explicit Method Overrides setting are no longer supported.
   The associated settings have been removed. Please save your upgraded Dotfuscator config.`

4. Salvare il file di configurazione dotfuscator aggiornato (CTRL+S).

5. Se si usa un sistema di controllo del codice sorgente, ad esempio Git, assicurarsi che le modifiche apportate al file di configurazione dotfuscator siano riflesse in tale sistema.
   Distribuire queste modifiche al resto del team in base alle esigenze del sistema e dell'organizzazione.

### <a name="update-xamarin-integration"></a>Aggiornare l'integrazione di Xamarin

Se Dotfuscator Community 5 è stato integrato nel [][xamarin-download] progetto [Xamarin,][xamarin] uno dei passaggi necessari per scaricare le destinazioni e le attività MSBuild personalizzate, ad esempio `PreEmptive.Dotfuscator.Xamarin.targets` . Queste destinazioni e attività sono state aggiornate in Dotfuscator Community 6, quindi sarà necessario sostituire le versioni precedenti con le nuove versioni.

Per aggiornare i file di integrazione di Xamarin:

1. Individuare la directory in cui sono stati scaricati inizialmente questi file.
   Nell'esempio [][xamarin-download] riportato nelle istruzioni viene utilizzata una sottodirectory denominata , ma è possibile che i file sono stati scaricati in una directory diversa, che potrebbe contenere anche file non correlati `PreEmptive.Dotfuscator.Xamarin` a Dotfuscator.

2. Nella directory del passaggio 1 eliminare i file correlati all'integrazione di Dotfuscator Xamarin.

3. Scaricare il file ZIP collegato alla versione corrente della sezione User Guide seguente: Scaricare il set personalizzato di MSBuild [Targets and Tasks for Dotfuscator][xamarin-download].

4. Estrarre il contenuto del file ZIP nella stessa directory specificata nel passaggio 1.

5. Se si usa un sistema di controllo del codice sorgente, ad esempio Git, assicurarsi che la rimozione dei file vecchi e l'aggiunta dei nuovi file siano riflesse in tale sistema.
   A seconda del tipo di sistema, queste modifiche possono essere visualizzate come file che modificano il contenuto, anziché essere sostituiti.
   Distribuire queste modifiche al resto del team in base alle esigenze del sistema e dell'organizzazione.

Altre sottosezioni in questa pagina si applicano anche ai progetti Xamarin, quindi assicurarsi di esaminare anche le istruzioni rimanenti di questa pagina.

### <a name="update-references-to-attribute-libraries"></a>Aggiornare i riferimenti alle librerie di attributi

Dotfuscator consente di configurare determinate funzionalità tramite [attributi .NET][dotnet-attributes] nel codice sorgente.
Se i progetti usavano tali attributi, potrebbe essere necessario aggiornarli per risolvere le modifiche in Dotfuscator 6.

#### <a name="obfuscation-attributes"></a>Attributi di offuscamento

Non sono state apportate modifiche agli [attributi di offuscamento][attributes-obfuscation]. Questi attributi sono definiti nelle librerie di classi di base .NET e Dotfuscator Community 6 continua a rispettarli.

<a name="steps-attrs-check"></a>

#### <a name="check-attributes"></a>Controllare gli attributi

La libreria contenente gli [attributi check è][attributes-checks] stata modificata. In Dotfuscator Community 5 è stato distribuito come file insieme a Dotfuscator stesso. A partire da Dotfuscator Community 6, viene invece distribuito come pacchetto NuGet pubblico.

Se si tenta di compilare un Visual Studio che fa ancora riferimento al percorso precedente, è possibile che si otterrà errori come gli esempi seguenti:

`The type or namespace name 'PreEmptive' could not be found
(are you missing a using directive or an assembly reference?)`

`The type or namespace name 'TamperCheckAttribute' could not be found
(are you missing a using directive or an assembly reference?)`

È anche possibile che venga visualizzato questo avviso:

`Could not resolve this reference. Could not locate the assembly "PreEmptive.Attributes". Check to make sure the assembly exists
on disk. If this reference is required by your code, you may get compilation errors.`

Per aggiornare il progetto in modo da usare il nuovo percorso:

1. Rimuovere il riferimento all'assembly del progetto in `PreEmptive.Attributes.dll` .

2. Aggiungere il NuGet al `PreEmptive.Protection.Checks.Attributes` progetto.
    Il pacchetto è disponibile nel feed NuGet predefinito, [nuget.org][nuget-org].

Sono stati rimossi anche i parametri di ogni `ExtendedKey` attributo Check.
Questi parametri sono stati ignorati in Dotfuscator Community 5, ma se il codice sorgente li ha usati indipendentemente, sarà necessario rimuovere questi utilizzi per consentire la compilazione del progetto.

<a name="steps-attrs-analytics"></a>

#### <a name="instrumentation-attributes"></a>Attributi di strumentazione

Gli attributi di strumentazione sono stati usati per configurare la funzionalità Di analisi preliminare in Dotfuscator 5. Tuttavia, PreEmptive Analytics è stato rimosso in Dotfuscator 6. vedere la sottosezione Funzionalità rimossa [PreEmptive Analytics](#removed-analytics). Di conseguenza, sono stati rimossi anche gli attributi di strumentazione.

Se si tenta di compilare un progetto Visual Studio che usa attributi di strumentazione, è possibile che vengano visualizzati gli stessi tipi di errori e avvisi specificati [in](#steps-attrs-check)Controlla attributi , anche se i nomi degli attributi saranno diversi (ad esempio, anziché `FeatureAttribute` `TamperCheckAttribute` ).

Se si tenta di eseguire Dotfuscator in assembly già compilati che contengono utilizzi di attributi di strumentazione, si otterranno errori come gli esempi seguenti:

`The PreEmptive.Attributes.FeatureAttribute attribute (annotating SomeNamespace.SomeType::SomeMethod) is not recognized
by this version of Dotfuscator.`

Per risolvere questi problemi, è necessario rimuovere tutti gli utilizzi degli attributi di strumentazione dal codice sorgente.
Sarà anche necessario rimuovere i riferimenti all'assembly alla libreria che ha definito gli attributi, `PreEmptive.Attributes.dll` .
Se si usavano anche gli attributi Check definiti in questa libreria, questi sono stati spostati. Vedere [Controllare gli attributi in](#steps-attrs-check) precedenza.

## <a name="removed-features"></a>Funzionalità rimosse

Dotfuscator Community 6 introduce modifiche di rilievo rispetto a Dotfuscator Community 5. Se si usa Dotfuscator Community 5, questa sezione descrive come gestire le modifiche che potrebbero richiedere modifiche alla compilazione o influire sull'output di Dotfuscator.

Un elenco completo delle modifiche è disponibile nel [log delle modifiche][changelog].

<a name="removed-analytics"></a>

### <a name="preemptive-analytics"></a>PreEmptive Analytics

Dotfuscator 6 non supporta l'analisi preliminare, incluso Il controllo dei dati di telemetria. Tuttavia, [i controlli stessi][checks-overview] (incluse le azioni di notifica [dell'applicazione][checks-notification] e [controllo)][checks-actions]sono ancora supportati.

Per usare Dotfuscator 6, è necessario aggiornare il file di [configurazione](#steps-config-files) per rimuovere le impostazioni di PreEmptive Analytics.

Se si usavano attributi nel codice per configurare PreEmptive Analytics, è necessario rimuoverli dal codice sorgente e ricompilare gli assembly di input prima che Dotfuscator 6 possa proteggere tali assembly. [](#steps-attrs-analytics)

Se si usa Controlla telemetria per segnalare quando un controllo rileva uno stato non valido (ad [][checks-notification] esempio quando viene rilevata una manomissione), [][tamper]è possibile sostituirlo con una notifica dell'applicazione personalizzata che segnala l'evento imprevisto a applicazione Azure Insights o [a][application-insights] un altro servizio di propria scelta.

### <a name="unsupported-application-types"></a>Tipi di applicazioni non supportati

I tipi di applicazione seguenti non sono più supportati in Dotfuscator 6:

* Windows Phone
* WinRT (Windows 8 app)
* Silverlight
* Unity (motore di gioco)

Inoltre, le app UWP (Universal Windows Platform) sono supportate solo per [gli scenari Xamarin.][xamarin]

Per proteggere altri tipi di app UWP, eseguire l'aggiornamento a [Dotfuscator Professional][pro] e seguire le istruzioni [per proteggere l'app.][pro-pya]

### <a name="unsupported-inputs"></a>Input non supportati

Dotfuscator Community non supporta più pacchetti UWP (Universal Windows Platform) `.appx` [come input][inputs]. È possibile continuare a proteggere le app Xamarin che hanno come destinazione la piattaforma UWP con [l'integrazione di Xamarin.][xamarin] Per proteggere altri tipi di app UWP, eseguire l'aggiornamento a [Dotfuscator Professional][pro] e seguire le istruzioni [per proteggere l'app.][pro-pya]

Inoltre, `.xap` i pacchetti non possono più essere usati come input perché Silverlight non è più supportato.

### <a name="introduce-explicit-method-overrides"></a>Introdurre override espliciti dei metodi

L'opzione Ridenominazione per introdurre override espliciti del metodo è stata rimossa da Dotfuscator. Per usare Dotfuscator 6, è necessario aggiornare [il file di configurazione](#steps-config-files) per rimuovere questa impostazione.

[changelog]: https://www.preemptive.com/support/dotfuscator-support/dotfuscator-ce-change-log
[download]: https://www.preemptive.com/products/dotfuscator/downloads
[always-improving]: https://www.preemptive.com/always-improving
[vs-update]: ../../install/update-visual-studio.md

[install]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html
[register]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_register.html
[pro]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[pro-pya]: https://www.preemptive.com/dotfuscator/pro/userguide/en/getting_started_protect.html

[gui]:  https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_gui.html
[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[xamarin]: https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html
[xamarin-download]: https://www.preemptive.com/dotfuscator/ce/docs/help/getting_started_xamarin.html#pctoc-download-the-custom-set-of-msbuild-targets-and-tasks-for-dotfuscator

[inputs]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_inputs.html

[checks-overview]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[checks-notification]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#pctoc-application-notification
[checks-actions]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#pctoc-check-actions
[tamper]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html

[attributes-checks]: https://www.preemptive.com/dotfuscator/ce/docs/help/attributes_checks.html
[attributes-obfuscation]: https://www.preemptive.com/dotfuscator/ce/docs/help/attributes_obfuscation.html

[verbosity]: ../how-to-view-save-and-configure-build-log-files.md#to-change-the-amount-of-information-included-in-the-build-log
[dotnet-attributes]: /dotnet/standard/attributes
[application-insights]: /azure/azure-monitor/app/app-insights-overview
[nuget-org]: https://www.nuget.org/
