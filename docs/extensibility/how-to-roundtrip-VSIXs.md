---
title: Come per le estensioni di round trip
ms.date: 06/25/2017
ms.topic: conceptual
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: gregvanl
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 1014d76473511df9b73cae371e5e5dea2364f8b2
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790420"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-2017-and-visual-studio-2015"></a>Procedura: Rendere compatibili con Visual Studio 2017 e Visual Studio 2015 le estensioni

Questo documento viene illustrato come creare progetti di estendibilità round trip tra Visual Studio 2015 e Visual Studio 2017. Dopo aver completato l'aggiornamento, un progetto sarà in grado di aprire, compilare, installare ed eseguire in Visual Studio 2015 e Visual Studio 2017. Come riferimento, alcune estensioni che è possono eseguire il round trip tra Visual Studio 2015 e Visual Studio 2017 sono disponibili i [esempi di estendibilità di Visual Studio SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Se si intende solo build in Visual Studio 2017, ma vuole che l'output VSIX per l'esecuzione in Visual Studio 2015 e Visual Studio 2017, quindi vedere il [documento di migrazione di estensione](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> A causa di modifiche in Visual Studio tra versioni diverse, alcune cose che ha lavorato in una versione non funzionano in un altro. Assicurarsi che le funzionalità che si sta provando ad accedere sono disponibili in entrambe le versioni o l'estensione avranno risultati imprevisti.

Ecco un riepilogo della procedura che si farà in questo documento, eseguire il round trip di un progetto VSIX:

1. Importare i pacchetti NuGet corretti.
2. Aggiornare il manifesto di estensione:
    * Destinazione di installazione
    * Prerequisiti
3. Aggiornare file CSProj:
    * Aggiornamento `<MinimumVisualStudioVersion>`.
    * Aggiungere il `<VsixType>` proprietà.
    * Aggiungere la proprietà di debug `($DevEnvDir)` 3 volte.
    * Aggiungere condizioni per l'importazione di destinazioni e strumenti di compilazione.

4. Compilazione e Test

## <a name="environment-setup"></a>Configurazione dell'ambiente

Questo documento presuppone che sia installato nel computer di quanto segue:

* Visual Studio 2015 con installato il SDK di Visual Studio
* Visual Studio 2017 con il carico di lavoro di estendibilità installato

## <a name="recommended-approach"></a>Approccio consigliato

Si consiglia di iniziare l'aggiornamento con Visual Studio 2015, invece di Visual Studio 2017. Il vantaggio principale di sviluppo in Visual Studio 2015 è garantire che non vi sono riferimenti degli assembly che non sono disponibili in Visual Studio 2015. Se si esegue l'operazione di sviluppo in Visual Studio 2017, sussiste il rischio che si potrebbe introdurre una dipendenza da un assembly che esiste solo in Visual Studio 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Assicurarsi che non sono presenti riferimenti a Project. JSON

Più avanti in questo documento, si inserirà le istruzioni di importazione condizionale in per i **file con estensione csproj* file. Questa operazione non funziona se i riferimenti NuGet vengono archiviati in *Project. JSON*. Di conseguenza, è consigliabile spostare tutti i riferimenti NuGet per la *Packages. config* file.
Se il progetto contiene un *Project. JSON* file:

* Prendere nota dei riferimenti nel *Project. JSON*.
* Dal **Esplora soluzioni**, eliminare il *Project. JSON* file dal progetto. Questa procedura elimina le *Project. JSON* file e lo rimuove dal progetto.
* Aggiungere che i riferimenti NuGet nuovamente al progetto:
    * Fare clic sui **soluzione** e scegliere **Gestisci pacchetti NuGet per la soluzione**.
    * Visual Studio crea automaticamente il *Packages. config* file automaticamente.

> [!NOTE]
> Se il progetto contiene i pacchetti di EnvDTE, devono essere aggiunti con il pulsante destro facendo clic su **riferimenti** selezionando **aggiungere riferimento** e l'aggiunta del riferimento appropriato. Uso di pacchetti NuGet può creare errori durante il tentativo di compilare il progetto.

## <a name="add-appropriate-build-tools"></a>Aggiungere gli strumenti di compilazione appropriato

È necessario per assicurarsi di aggiungere strumenti di compilazione che ci consentirà di compilare ed eseguire il debug in modo appropriato. Microsoft ha creato un assembly per questa chiamata Microsoft.VisualStudio.Sdk.BuildTasks.

Per compilare e distribuire un VSIXv3 in Visual Studio 2015 e 2017, sono necessari i pacchetti NuGet seguenti:

Versione | Strumenti predefiniti
--- | ---
Visual Studio 2015 | Microsoft.VisualStudio.Sdk.BuildTasks.14.0
Visual Studio 2017 | Microsoft.VSSDK.BuildTool

A tale scopo:

* Aggiungere il pacchetto NuGet Microsoft.VisualStudio.Sdk.BuildTasks.14.0 al progetto.
* Se il progetto non contiene Microsoft.VSSDK.BuildTools, aggiungerlo.
* Verificare la versione Microsoft.VSSDK.BuildTools sia 15.x o versione successiva.

## <a name="update-extension-manifest"></a>Aggiorna manifesto dell'estensione

### <a name="1-installation-targets"></a>1. Destinazioni di installazione:

È necessario indicare a Visual Studio quali versioni di destinazione per la creazione di un progetto VSIX. In genere, questi riferimenti sono in versione 14.0 (Visual Studio 2015), versione 15.0 (Visual Studio 2017) o versione 16.0 (Visual Studio 2019). In questo caso, si vuole compilare un'estensione VSIX che consentirà di installare un'estensione per entrambe, pertanto è necessario specificare entrambe le versioni. Se si desidera VSIX per compilare e installare nelle versioni precedenti a 14.0, questa operazione può essere eseguita impostando il numero di versione precedente. Tuttavia, 10.0 e versioni precedenti non sono più supportate.

* Aprire il *vsixmanifest* file in Visual Studio.
* Aprire il **destinazioni di installazione** scheda.
* Modifica il **intervallo di versioni** per [14,0, 17.0). Il ' [' indica a Visual Studio per includere 14,0 e tutte le versioni precedenti si. il ')' indica a Visual Studio per includere tutte le versioni fino a, ma non incluse, versione 17.0.
* Salvare tutte le modifiche e chiudere tutte le istanze di Visual Studio.

![Immagine di destinazioni di installazione](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. Aggiunta dei prerequisiti per la *Extension. vsixmanifest* file

È necessario l'Editor principale di Visual Studio come prerequisito. Aprire Visual Studio e usare la finestra di progettazione manifesto aggiornato per inserire i prerequisiti.

Per eseguire questa operazione manualmente:

* Passare alla directory del progetto in Esplora File.
* Aprire il *Extension. vsixmanifest* file con un editor di testo.
* Aggiungere il seguente tag:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Salvare e chiudere il file.

> [!NOTE]
> Potrebbe essere necessario modificare manualmente la versione del prerequisito per assicurarsi che sia compatibile con tutte le versioni di Visual Studio 2017. Questo avviene perché la finestra di progettazione inserisce la versione minima come la versione corrente di Visual Studio (ad esempio, 15.0.26208.0). Tuttavia, poiché gli altri utenti potrebbero avere una versione precedente, si dovranno modificare manualmente questo 15.0.

A questo punto, il file manifesto dovrebbe essere simile al seguente:

![Esempio di prerequisiti](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificare il file di progetto (MyProject. csproj)

È altamente consigliabile avere un riferimento a un file con estensione csproj modificato aperto durante l'esecuzione di questo passaggio. È possibile trovare alcuni esempi [qui](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Selezionare un campione di estensibilità, trovare il *file con estensione csproj* file per riferimento ed eseguire i passaggi seguenti:

* Passare alla directory del progetto in **Esplora File**.
* Aprire il *MyProject. csproj* file con un editor di testo.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. Aggiornare il MinimumVisualStudioVersion

* Impostare la versione minima di visual studio su `$(VisualStudioVersion)` e aggiungere un'istruzione condizionale per il. Se non sono presenti, aggiungere questi tag. Verificare che i tag siano impostati come indicato di seguito:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. Aggiungere la proprietà VsixType.

* Aggiungere il seguente tag `<VsixType>v3</VsixType>` a un gruppo di proprietà.

> [!NOTE]
> È consigliabile aggiungere quanto segue sotto il `<OutputType></OutputType>` tag.

### <a name="3-add-the-debugging-properties"></a>3. Aggiungere le proprietà di debug

* Aggiungere il gruppo di proprietà seguente:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartPrograms>$(DevEnvDir)devenv.exe</StartPrograms>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminare tutte le istanze dell'esempio di codice seguente dal *file con estensione csproj* file ed eventuali *. csproj* file:

```xml
<StartAction>Program</StartAction>
<StartPrograms>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartPrograms>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. Aggiungere le condizioni per le importazioni di strumenti di compilazione

* Aggiungere altre istruzioni condizionali per il `<import>` tag che hanno un riferimento Microsoft.VSSDK.BuildTools. Inserisci `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione della condizione. Queste istruzioni verranno visualizzati nell'intestazione e piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Aggiungere altre istruzioni condizionali per il `<import>` tag che hanno un Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Inserisci `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione della condizione. Queste istruzioni verranno visualizzati nell'intestazione e piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Aggiungere altre istruzioni condizionali per il `<Error>` tag che hanno un riferimento Microsoft.VSSDK.BuildTools. Eseguire questa operazione inserendo `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione della condizione. Queste istruzioni verranno visualizzati nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Aggiungere altre istruzioni condizionali per il `<Error>` tag che hanno un Microsoft.VisualStudio.Sdk.BuildTasks.14.0. Inserisci `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione della condizione. Queste istruzioni verranno visualizzati nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Salvare il file csproj e chiuderlo.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2017"></a>Installa l'estensione di test in Visual Studio 2015 e Visual Studio 2017

A questo punto, il progetto deve essere pronto a compilare un VSIXv3 che è possibile installare su Visual Studio 2015 e Visual Studio 2017.

* Aprire il progetto in Visual Studio 2015.
* Compilare il progetto e verificare l'output indica che un progetto VSIX compilato correttamente.
* Passare alla directory del progetto.
* Aprire il *\bin\Debug* cartella.
* Fare doppio clic sul file VSIX e installare l'estensione in Visual Studio 2015 e Visual Studio 2017.
* Assicurarsi che sia possibile visualizzare l'estensione nella **degli strumenti** > **estensioni e aggiornamenti** nel **installato** sezione.
* Tentativo di esecuzione/usare l'estensione per verificare il corretto funzionamento.

![Trovare un progetto VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Se si blocca il progetto con il messaggio **apertura del file**, forza arresto Visual Studio, passare alla directory del progetto, cartelle nascoste visualizzare ed eliminare il *VS* cartella.