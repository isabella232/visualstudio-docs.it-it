---
title: Come eseguire il round trip delle estensioni
description: Informazioni su come eseguire il round trip di progetti di estendibilità di Visual Studio tra Visual Studio 2015 e Visual Studio 2019 o Visual Studio 2017.
ms.custom: SEO-VS-2020
ms.date: 06/25/2017
ms.topic: how-to
ms.assetid: 2d6cf53c-011e-4c9e-9935-417edca8c486
author: willbrown
ms.author: madsk
manager: justinclareburt
ms.workload:
- willbrown
ms.openlocfilehash: 3db3264bf5226b5679452659928e451e7975b001
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993614"
---
# <a name="how-to-make-extensions-compatible-with-visual-studio-20192017-and-visual-studio-2015"></a>Procedura: rendere compatibili le estensioni con Visual Studio 2019/2017 e Visual Studio 2015

Questo documento illustra come eseguire il round trip di progetti di estensibilità tra Visual Studio 2015 e Visual Studio 2019 o Visual Studio 2017. Al termine dell'aggiornamento, un progetto sarà in grado di aprire, compilare, installare ed eseguire in Visual Studio 2015 e Visual Studio 2019 o 2017. Per informazioni di riferimento, alcune estensioni che possono essere completate tra Visual Studio 2015 e Visual Studio 2019 o 2017 sono disponibili negli [esempi di estendibilità di vs SDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Se si intende compilare solo in Visual Studio 2019/2017, ma si vuole che l'output VSIX venga eseguito sia in Visual Studio 2015 che in Visual Studio 2019/2017, fare riferimento al [documento di migrazione dell'estensione](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

> [!NOTE]
> A causa delle modifiche apportate a Visual Studio tra le versioni, alcune operazioni che hanno funzionato in una versione non funzionano in un'altra. Verificare che le funzionalità a cui si sta tentando di accedere siano disponibili in entrambe le versioni oppure che l'estensione abbia risultati imprevisti.

Ecco una descrizione dei passaggi da completare in questo documento per eseguire il round trip di un progetto VSIX:

1. Importa i pacchetti NuGet corretti.
2. Manifesto dell'estensione di aggiornamento:
    * Destinazione installazione
    * Prerequisiti
3. Aggiorna CSProj:
    * Aggiornare `<MinimumVisualStudioVersion>`.
    * Aggiungere la proprietà `<VsixType>`.
    * Aggiungere la proprietà di debug `($DevEnvDir)` 3 volte.
    * Aggiungere le condizioni per l'importazione di strumenti e destinazioni di compilazione.

4. Compilazione e test

## <a name="environment-setup"></a>Configurazione dell'ambiente

In questo documento si presuppone che nel computer siano installati gli elementi seguenti:

* Visual Studio 2015 con VS SDK installato
* Visual Studio 2019 o 2017 con il carico di lavoro estensibilità installato

## <a name="recommended-approach"></a>Approccio consigliato

È consigliabile avviare questo aggiornamento con Visual Studio 2015, anziché Visual Studio 2019 o 2017. Il vantaggio principale dello sviluppo in Visual Studio 2015 consiste nel garantire che non si faccia riferimento ad assembly non disponibili in Visual Studio 2015. Se si esegue lo sviluppo in Visual Studio 2019 o 2017, esiste il rischio che si possa introdurre una dipendenza da un assembly presente solo in Visual Studio 2019 o 2017.

## <a name="ensure-there-is-no-reference-to-projectjson"></a>Verificare che non sia presente alcun riferimento a project.jsin

Più avanti in questo documento, le istruzioni di importazione condizionale vengono inserite nel file **. csproj* . Questa operazione non funzionerà se i riferimenti NuGet vengono archiviati in *project.js*. Di conseguenza, è consigliabile spostare tutti i riferimenti NuGet al file *packages.config* .
Se il progetto contiene un *project.jssu* file:

* Prendere nota dei riferimenti in *project.js*.
* Dal **Esplora soluzioni** eliminare il *project.jssul* file dal progetto. Questa operazione consente di eliminare il *project.jsnel* file e di rimuoverlo dal progetto.
* Aggiungere di nuovo i riferimenti NuGet al progetto:
  * Fare clic con il pulsante destro del mouse sulla **soluzione** e scegliere **Gestisci pacchetti NuGet per la soluzione**.
  * Visual Studio crea automaticamente il file di *packages.config* .

> [!NOTE]
> Se il progetto contiene pacchetti EnvDTE, potrebbe essere necessario aggiungerli facendo clic con il pulsante destro del mouse su **riferimenti** selezionando **Aggiungi riferimento** e aggiungendo il riferimento appropriato. L'uso di pacchetti NuGet può creare errori durante il tentativo di compilare il progetto.

## <a name="add-appropriate-build-tools"></a>Aggiungere gli strumenti di compilazione appropriati

È necessario assicurarsi di aggiungere gli strumenti di compilazione che ci consentiranno di compilare ed eseguire il debug in modo appropriato. Microsoft ha creato un assembly per questo oggetto denominato Microsoft. VisualStudio. Sdk. BuildTasks.

Per compilare e distribuire un VSIXv3 in Visual Studio 2015 e 2019/2017, sono necessari i pacchetti NuGet seguenti:

Versione | Strumenti compilati
--- | ---
Visual Studio 2015 | Microsoft. VisualStudio. Sdk. BuildTasks. 14.0
Visual Studio 2019 o 2017 | Microsoft. VSSDK. BuildTool

A tale scopo, procedere nel seguente modo:

* Aggiungere il pacchetto NuGet Microsoft. VisualStudio. Sdk. BuildTasks. 14.0 al progetto.
* Se il progetto non contiene Microsoft. VSSDK. BuildTools, aggiungerlo.
* Verificare che la versione di Microsoft. VSSDK. BuildTools sia 15. x o successiva.

## <a name="update-extension-manifest"></a>Aggiorna manifesto dell'estensione

### <a name="1-installation-targets"></a>1. destinazioni di installazione

È necessario indicare a Visual Studio le versioni di destinazione per la compilazione di un progetto VSIX. In genere, questi riferimenti sono alla versione 14,0 (Visual Studio 2015), alla versione 15,0 (Visual Studio 2017) o alla versione 16,0 (Visual Studio 2019). In questo caso, si vuole creare un progetto VSIX che installerà un'estensione per entrambi, quindi è necessario specificare come destinazione entrambe le versioni. Se si vuole che il progetto VSIX venga compilato e installato nelle versioni precedenti alla 14,0, è possibile eseguire questa operazione impostando il numero di versione precedente; Tuttavia, la versione 10,0 e versioni precedenti non sono più supportate.

* Aprire il file *source. Extension. vsixmanifest* in Visual Studio.
* Aprire la scheda **destinazioni di installazione** .
* Modificare l' **intervallo di versioni** in [14,0, 17,0). Il ' [' indica a Visual Studio di includere 14,0 e tutte le versioni precedenti. Il ')' indica a Visual Studio di includere tutte le versioni fino a, ma non includendo la versione 17,0.
* Salvare tutte le modifiche e chiudere tutte le istanze di Visual Studio.

![Immagine delle destinazioni di installazione](media/visual-studio-installation-targets-example.png)

### <a name="2-adding-prerequisites-to-the-extensionvsixmanifest-file"></a>2. aggiunta dei prerequisiti al file *Extension. vsixmanifest*

Come prerequisito è necessario l'editor principale di Visual Studio. Aprire Visual Studio e usare la finestra di progettazione del manifesto aggiornata per inserire i prerequisiti.

Per eseguire questa operazione manualmente:

* Passare alla directory del progetto in Esplora file.
* Aprire il file *Extension. vsixmanifest* con un editor di testo.
* Aggiungere il tag seguente:

```xml
<Prerequisites>
    <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" DisplayName="Visual Studio core editor" />
</Prerequisites>
```

* Salvare e chiudere il file.

> [!NOTE]
> Potrebbe essere necessario modificare manualmente la versione dei prerequisiti per assicurarsi che sia compatibile con tutte le versioni di Visual Studio 2019 o 2017. Questo perché la finestra di progettazione inserirà la versione minima come versione corrente di Visual Studio (ad esempio, 15.0.26208.0). Tuttavia, poiché altri utenti possono avere una versione precedente, è necessario modificarlo manualmente in 15,0.

A questo punto, il file manifesto avrà un aspetto simile al seguente:

![Esempio di prerequisiti](media/visual-studio-prerequisites-example.png)

## <a name="modify-the-project-file-myprojectcsproj"></a>Modificare il file di progetto (MyProject. csproj)

Quando si esegue questo passaggio, è consigliabile avere un riferimento a un. csproj modificato. [Qui](https://github.com/Microsoft/VSSDK-Extensibility-Samples)è possibile trovare alcuni esempi. Selezionare un esempio di estendibilità, trovare il file con *estensione csproj* per riferimento ed eseguire i passaggi seguenti:

* Passare alla directory del progetto in **Esplora file**.
* Aprire il file *MyProject. csproj* con un editor di testo.

### <a name="1-update-the-minimumvisualstudioversion"></a>1. aggiornare MinimumVisualStudioVersion

* Impostare la versione minima di Visual Studio su `$(VisualStudioVersion)` e aggiungervi un'istruzione condizionale. Aggiungere questi tag se non esistono. Verificare che i tag siano impostati nel modo seguente:

```xml
<VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">14.0</VisualStudioVersion>
<MinimumVisualStudioVersion>$(VisualStudioVersion)</MinimumVisualStudioVersion>
```

### <a name="2-add-the-vsixtype-property"></a>2. aggiungere la proprietà VsixType.

* Aggiungere il seguente tag `<VsixType>v3</VsixType>` a un gruppo di proprietà.

> [!NOTE]
> È consigliabile aggiungerlo sotto il `<OutputType></OutputType>` tag.

### <a name="3-add-the-debugging-properties"></a>3. aggiungere le proprietà di debug

* Aggiungere il gruppo di proprietà seguente:

```xml
<PropertyGroup>
    <StartAction>Program</StartAction>
    <StartProgram>$(DevEnvDir)devenv.exe</StartProgram>
    <StartArguments>/rootsuffix Exp</StartArguments>
</PropertyGroup>
```

* Eliminare tutte le istanze dell'esempio di codice seguente dal file con estensione *csproj* e da qualsiasi file con *estensione csproj. User* :

```xml
<StartAction>Program</StartAction>
<StartProgram>$(ProgramFiles)\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe</StartProgram>
<StartArguments>/rootsuffix Exp</StartArguments>
```

### <a name="4-add-conditions-to-the-build-tools-imports"></a>4. aggiungere condizioni alle importazioni degli strumenti di compilazione

* Aggiungere altre istruzioni condizionali ai `<import>` tag con un riferimento Microsoft. VSSDK. BuildTools. Inserire `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione Condition. Queste istruzioni verranno visualizzate nell'intestazione e nel piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VSSDK.BuildTools.15.0.26201…" Condition="'$(VisualStudioVersion)' != '14.0' And Exists(…" />
```

* Aggiungere altre istruzioni condizionali ai `<import>` tag con Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Inserire `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione Condition. Queste istruzioni verranno visualizzate nell'intestazione e nel piè di pagina del file csproj.

Ad esempio:

```xml
<Import Project="packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" Condition="'$(VisualStudioVersion)' == '14.0' And Exists(…" />
```

* Aggiungere altre istruzioni condizionali ai `<Error>` tag con un riferimento Microsoft. VSSDK. BuildTools. Eseguire questa operazione inserendo `'$(VisualStudioVersion)' != '14.0' And` all'inizio dell'istruzione Condition. Queste istruzioni verranno visualizzate nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' != '14.0' And Exists('packages\Microsoft.VSSDK.BuildTools.15.0.26201…" />
```

* Aggiungere altre istruzioni condizionali ai `<Error>` tag con Microsoft. VisualStudio. Sdk. BuildTasks. 14.0. Inserire `'$(VisualStudioVersion)' == '14.0' And` all'inizio dell'istruzione Condition. Queste istruzioni verranno visualizzate nel piè di pagina del file csproj.

Ad esempio:

```xml
<Error Condition="'$(VisualStudioVersion)' == '14.0' And Exists('packages\Microsoft.VisualStudio.Sdk.BuildTasks.14.0.14.0…" />
```

* Salvare il file csproj e chiuderlo. 
  * Si noti che se si usa più di un progetto nella soluzione, impostare questo progetto come progetto di avvio usando "Imposta come progetto di avvio" nel menu di scelta rapida del progetto. In questo modo si garantisce che Visual Studio riapra questo progetto dopo averlo scaricato.

## <a name="test-the-extension-installs-in-visual-studio-2015-and-visual-studio-2019-or-2017"></a>Testare l'installazione dell'estensione in Visual Studio 2015 e Visual Studio 2019 o 2017

A questo punto, il progetto dovrebbe essere pronto per compilare un VSIXv3 che può essere installato sia in Visual Studio 2015 che in Visual Studio 2017.

* Aprire il progetto in Visual Studio 2015.
* Compilare il progetto e verificare nell'output che un progetto VSIX venga compilato correttamente.
* Passare alla directory del progetto.
* Aprire la cartella *\bin\Debug* .
* Fare doppio clic sul file VSIX e installare l'estensione in Visual Studio 2015 e Visual Studio 2019/2017.
* Verificare che l'estensione sia visibile in **strumenti**  >  **estensioni e aggiornamenti** nella sezione **installazione** .
* Provare a eseguire/utilizzare l'estensione per verificarne il funzionamento.

![Trovare un progetto VSIX](media/finding-a-VSIX-example.png)

> [!NOTE]
> Se il progetto smette di rispondere con il messaggio di **apertura del file**, forzare l'arresto di Visual Studio, passare alla directory del progetto, visualizzare le cartelle nascoste ed eliminare la cartella *. vs* .
