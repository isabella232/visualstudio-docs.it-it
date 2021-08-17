---
title: Come eseguire il roundtrip delle estensioni
description: Informazioni su come eseguire Visual Studio round trip di progetti di estendibilità tra Visual Studio 2015 e Visual Studio 2019 o Visual Studio 2017.
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: a5430271875917c890477a13e67056052ed382ee26546ef7536909866f0e8346
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401706"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Procedura: Rendere le estensioni compatibili con Visual Studio 2019/2017 e Visual Studio 2015

Questo documento illustra come eseguire il round trip di progetti di estendibilità tra Visual Studio 2015 e Visual Studio 2019 o Visual Studio 2017. Al termine dell'aggiornamento, un progetto sarà in grado di aprire, compilare, installare ed eseguire sia in Visual Studio 2015 che Visual Studio 2019 o 2017. Come riferimento, alcune estensioni che possono essere round trip tra Visual Studio 2015 e Visual Studio 2019 o 2017 sono disponibili negli esempi di estendibilità di [VS SDK.](https://github.com/Microsoft/VSSDK-Extensibility-Samples)

Se si prevede di compilare solo Visual Studio Visual Studio 2019/2017, ma si vuole che il vsix di output sia in Visual Studio 2015 che in Visual Studio 2019/2017, fare riferimento al documento sulla migrazione dell'estensione [.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

> [!NOTE]
> A causa delle modifiche Visual Studio versioni, alcuni elementi che funzionavano in una versione non funzionano in un'altra. Assicurarsi che le funzionalità a cui si sta tentando di accedere siano disponibili in entrambe le versioni o che l'estensione abbia risultati imprevisti.

Ecco una descrizione dei passaggi che verranno completati in questo documento per eseguire il round trip di un vsix:

1. Importare i NuGet corretti.
2. Aggiornare il manifesto dell'estensione:
    * Destinazione di installazione
    * Prerequisiti
3. Aggiornare CSProj:
    * Aggiornare `<MinimumVisualStudioVersion>`.
    * Aggiungere la proprietà `<VsixType>`.
    * Aggiungere la proprietà di debug `($DevEnvDir)` 3 volte.
    * Aggiungere condizioni per l'importazione di strumenti di compilazione e destinazioni.

4. Compilazione e test

## <a name="environment-setup"></a>Configurazione dell'ambiente

Questo documento presuppone che nel computer sia installato quanto segue:

* Visual Studio 2015 con VS SDK installato
* Visual Studio 2019 o 2017 con il carico di lavoro Extensibility installato

## <a name="recommended-approach"></a>Approccio consigliato

È consigliabile avviare questo aggiornamento con Visual Studio 2015, anziché Visual Studio 2019 o 2017. Il principale vantaggio dello sviluppo Visual Studio 2015 è assicurarsi di non fare riferimento ad assembly non disponibili in Visual Studio 2015. Se si fa sviluppo in Visual Studio 2019 o 2017, esiste il rischio di introdurre una dipendenza da un assembly esistente solo Visual Studio 2019 o 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Assicurarsi che non sia presente alcun riferimento project.jssu

Più avanti in questo documento verranno inserite istruzioni di importazione condizionale nel file **con estensione csproj.* Questa operazione non funziona se i NuGet vengono archiviati inproject.js *in*. Di conseguenza, è consigliabile spostare tutti NuGet riferimenti al file *packages.config* file.
Se il progetto contiene un *project.jsfile:*

* Prendere nota dei riferimenti inproject.js *in*.
* Dal **Esplora soluzioni** eliminare ilproject.js *file* dal progetto. In questo modo il *project.jsnel* file e lo rimuove dal progetto.
* Aggiungere nuovamente NuGet riferimenti al progetto:
  * Fare clic con il pulsante destro **del mouse** sulla soluzione e scegliere Gestisci NuGet pacchetti per **la soluzione**.
  * Visual Studio il file *packages.config* automaticamente.

> [!NOTE]
> Se il progetto contiene pacchetti EnvDTE, potrebbe essere necessario aggiungerli facendo clic con il pulsante destro del mouse su **Riferimenti** selezionando **Aggiungi** riferimento e aggiungendo il riferimento appropriato. L NuGet i pacchetti possono creare errori durante il tentativo di compilare il progetto.

## <a name="add-appropriate-build-tools"></a>Aggiungere gli strumenti di compilazione appropriati

È necessario assicurarsi di aggiungere strumenti di compilazione che consentano di compilare ed eseguire il debug in modo appropriato. Microsoft ha creato un assembly denominato Microsoft.VisualStudio.Sdk.BuildTasks.

Per compilare e distribuire un vsixv3 in Visual Studio 2015 e 2019/2017, sono necessari i pacchetti NuGet seguenti:

Versione | Strumenti compilati
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2019 o 2017 | Microsoft.VSSDK.BuildTool

A tale scopo, procedere nel seguente modo:

* Aggiungere il NuGet pacchetto Microsoft.VisualStudio.Sdk.BuildTasks.14.0 al progetto.
* Se il progetto non contiene Microsoft.VSSDK.BuildTools, aggiungerlo.
* Verificare che la versione di Microsoft.VSSDK.BuildTools sia 15.x o successiva.

## <a name="update-extension-manifest"></a>Aggiornare il manifesto dell'estensione

### <a name="1-installation-targets"></a>1. Destinazioni di installazione

È necessario indicare Visual Studio le versioni di destinazione per la compilazione di un vsix. In genere, questi riferimenti sono alla versione 14.0 (Visual Studio 2015), alla versione 15.0 (Visual Studio 2017) o alla versione 16.0 (Visual Studio 2019). In questo caso, si vuole compilare un vsix che installerà un'estensione per entrambe le versioni, quindi è necessario scegliere come destinazione entrambe le versioni. Per compilare e installare VSIX in versioni precedenti alla 14.0, è possibile impostare il numero di versione precedente. Tuttavia, la versione 10.0 e precedenti non sono più supportate.

* Aprire il file *source.extension.vsixmanifest* in Visual Studio.
* Aprire la **scheda Destinazioni di** installazione.
* Modificare **l'intervallo di** versioni in [14.0, 17.0). '[' indica Visual Studio includere la versione 14.0 e tutte le versioni precedenti. ')' indica Visual Studio includere tutte le versioni fino alla versione 17.0, ma non inclusa.
* Salvare tutte le modifiche e chiudere tutte le istanze di Visual Studio.

![Immagine delle destinazioni di installazione](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Aggiunta dei prerequisiti al file *extension.vsixmanifest*

L'editor Visual Studio Core è necessario come prerequisito. Aprire Visual Studio e usare la finestra di progettazione del manifesto aggiornata per inserire i prerequisiti.

Per eseguire questa operazione manualmente:

* Passare alla directory del progetto in Esplora file.
* Aprire il file *extension.vsixmanifest* con un editor di testo.
* Aggiungere il tag seguente:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Salvare e chiudere il file.

> [!NOTE]
> Potrebbe essere necessario modificare manualmente la versione prerequisita per assicurarsi che sia compatibile con tutte le versioni di Visual Studio 2019 o 2017. Questo perché la finestra di progettazione inserirà la versione minima come versione corrente di Visual Studio (ad esempio, 15.0.26208.0). Tuttavia, poiché altri utenti potrebbero avere una versione precedente, è necessario modificarla manualmente nella versione 15.0.

A questo punto, il file manifesto dovrebbe essere simile al seguente:

![Esempio di prerequisiti](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificare il file di progetto (myproject.csproj)

È consigliabile avere aperto un riferimento a un file con estensione csproj modificato durante questo passaggio. È possibile trovare diversi esempi [qui.](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Selezionare un esempio di estendibilità, trovare il file *con estensione csproj* come riferimento ed eseguire la procedura seguente:

* Passare alla directory del progetto in **Esplora file**.
* Aprire il file *myproject.csproj* con un editor di testo.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aggiornare MinimumVisualStudioVersion

* Impostare la versione minima di Visual Studio su `$(VisualStudioVersion)` e aggiungere un'istruzione condizionale. Aggiungere questi tag se non esistono. Assicurarsi che i tag siano impostati come indicato di seguito:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Aggiungere la proprietà VsixType.

* Aggiungere il tag seguente `<VsixType>v3</VsixType>` a un gruppo di proprietà.

> [!NOTE]
> È consigliabile aggiungerlo sotto il `<OutputType></OutputType>` tag .

### <a name="3-add-the-debugging-properties"></a>3. Aggiungere le proprietà di debug

* Aggiungere il gruppo di proprietà seguente:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminare tutte le istanze dell'esempio di codice seguente dal file *con estensione csproj* e da tutti i file *con estensione csproj.user:*

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Aggiungere condizioni alle importazioni degli strumenti di compilazione

* Aggiungere istruzioni condizionali aggiuntive ai `<import>` tag con un riferimento Microsoft.VSSDK.BuildTools. Inserire `'$(VisualStudioVersion)' != '14.0' And` nella parte anteriore dell'istruzione della condizione. Queste istruzioni verranno visualizzate nell'intestazione e nel piè di pagina del file csproj.

Esempio:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Aggiungere istruzioni condizionali aggiuntive ai `<import>` tag con Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Inserire `'$(VisualStudioVersion)' == '14.0' And` nella parte anteriore dell'istruzione della condizione. Queste istruzioni verranno visualizzate nell'intestazione e nel piè di pagina del file csproj.

Esempio:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Aggiungere istruzioni condizionali aggiuntive ai tag con un `<Error>` riferimento Microsoft.VSSDK.BuildTools. A tale scopo, inserire `'$(VisualStudioVersion)' != '14.0' And` nella parte anteriore dell'istruzione della condizione. Queste istruzioni verranno visualizzate nel piè di pagina del file csproj.

Esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Aggiungere istruzioni condizionali aggiuntive ai `<Error>` tag con Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Inserire `'$(VisualStudioVersion)' == '14.0' And` nella parte anteriore dell'istruzione della condizione. Queste istruzioni verranno visualizzate nel piè di pagina del file csproj.

Esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Salvare il file csproj e chiuderlo. 
  * Si noti che se si usano più progetti nella soluzione, impostare questo progetto come Project di avvio usando "Imposta come Project di avvio" nel menu di scelta rapida del progetto). In questo modo si Visual Studio riapre il progetto dopo lo scaricamento.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Testare le installazioni dell'estensione Visual Studio 2015 e Visual Studio 2019 o 2017

A questo punto, il progetto deve essere pronto per compilare un vsixv3 che può essere installato in Visual Studio 2015 e Visual Studio 2017.

* Aprire il progetto in Visual Studio 2015.
* Compilare il progetto e verificare nell'output che un VSIX venga compilato correttamente.
* Passare alla directory del progetto.
* Aprire la *cartella \bin\Debug.*
* Fare doppio clic sul file VSIX e installare l'estensione in Visual Studio 2015 e Visual Studio 2019/2017.
* Assicurarsi di poter visualizzare l'estensione in **Estensioni** e aggiornamenti degli  >   strumenti nella **sezione** Installato.
* Provare a eseguire/usare l'estensione per verificare che funzioni.

![Trovare un vsix](media/finding-a-VSIX-example.png)

> [!NOTE]
> Se il progetto smette di rispondere con il messaggio che apre il **file**, forzare l'arresto Visual Studio, passare alla directory del progetto, visualizzare le cartelle nascoste ed eliminare *la cartella vs.*
