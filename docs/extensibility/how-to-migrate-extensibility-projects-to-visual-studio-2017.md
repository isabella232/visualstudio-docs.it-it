---
title: 'Procedura: eseguire la migrazione di progetti di estensibilità a Visual Studio 2017 Documenti Microsoft'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710989"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017How to: Migrate extensibility projects to Visual Studio 2017

In questo documento viene illustrato come aggiornare i progetti di estendibilità a Visual Studio 2017.This document explains how to upgrade extensibility projects to Visual Studio 2017. Oltre a descrivere come aggiornare i file di progetto, viene descritto anche come eseguire l'aggiornamento dal manifesto di estensione versione 2 (VSIX v2) al nuovo formato di manifesto VSIX versione 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installare Visual Studio 2017 con i carichi di lavoro necessariInstall Visual Studio 2017 with required workloads

Assicurarsi che l'installazione includa i carichi di lavoro seguenti:Make sure your installation includes the following workloads:

* Sviluppo per desktop .NET
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire la soluzione VSIX in Visual Studio 2017Open VSIX Solution in Visual Studio 2017

Tutti i progetti VSIX richiederanno un aggiornamento unidirezionale versione principale a Visual Studio 2017.All VSIX projects will require a major version one-way upgrade to Visual Studio 2017.

Verrà aggiornato il file di progetto (ad esempio *, con estensione csproj*):

* MinimumVisualStudioVersion - ora impostato su 15.0
* OldToolsVersion (se esiste in precedenza) - ora impostato su 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto Microsoft.VSSDK.BuildTools NuGet

> [!Note]
> Se la soluzione non fa riferimento al pacchetto Microsoft.VSSDK.BuildTools NuGet, è possibile ignorare questo passaggio.

Per compilare l'estensione nel nuovo formato VSIX v3 (versione 3), la soluzione dovrà essere compilata con i nuovi strumenti di compilazione VSSDK. Verrà installato con Visual Studio 2017, ma l'estensione VSIX v2 potrebbe contenere un riferimento a una versione precedente tramite NuGet.This will be installed with Visual Studio 2017, but your VSIX v2 extension might be holding a reference to an older version via NuGet. In tal caso, sarà necessario installare manualmente un aggiornamento del pacchetto Microsoft.VSSDK.BuildTools NuGet per la soluzione.

Per aggiornare i riferimenti NuGet a Microsoft.VSSDK.BuildTools:

* Fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet per soluzione**.
* Passare alla scheda **Aggiornamenti.**
* Selezionare **Microsoft.VSSDK.BuildTools (versione più recente)**.
* Premere **Aggiorna**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportare modifiche al manifesto dell'estensione VSIX

Per garantire che l'installazione dell'utente di Visual Studio disponga di tutti gli assembly necessari per eseguire l'estensione, specificare tutti i componenti o i pacchetti dei prerequisiti nel file manifesto dell'estensione. Quando un utente tenta di installare l'estensione, il VSIXInstaller controllerà se tutti i prerequisiti sono installati. Se alcuni sono mancanti, all'utente verrà richiesto di installare i componenti mancanti come parte del processo di installazione dell'estensione.

> [!Note]
> Come minimo, tutte le estensioni devono specificare il componente editor principale di Visual Studio come prerequisito.

* Modificare il file manifesto di estensione (in genere denominato *source.extension.vsixmanifest*).
* Assicurarsi che `InstallationTarget` includa 15.0.
* Aggiungere i prerequisiti di installazione necessari (come illustrato nell'esempio seguente).
  * È consigliabile specificare solo gli ID componente per i prerequisiti di installazione.
  * Vedere la sezione alla fine di questo documento per [istruzioni sull'identificazione degli ID dei componenti](#find-component-ids).

Esempio:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opzione: usare la finestra di progettazione per apportare modifiche al manifesto dell'estensione VSIXOption: Use the designer to make changes to the VSIX extension manifest

Anziché modificare direttamente il codice XML del manifesto, è possibile utilizzare la nuova scheda **Prerequisiti** in Progettazione manifesto per selezionare i prerequisiti e il codice XML verrà aggiornato.

> [!Note]
> Progettazione manifesto consente solo di selezionare i componenti (non carichi di lavoro o pacchetti) installati nell'istanza corrente di Visual Studio. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente non attualmente installato, modificare direttamente il codice XML del manifesto.

* Aprire il file *source.extension.vsixmanifest [Design].*
* Selezionare la scheda **Prerequisiti** e premere il pulsante **Nuovo.Select** Prerequisites tab and choose New button.

   ![Finestra di progettazione del manifesto VSIX](media/vsix-manifest-designer.png)

* Si aprirà la finestra **Aggiungi nuovo prerequisito.**

   ![aggiungere prerequisiti vsix](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a discesa **nome** e selezionare il prerequisito desiderato.
* Se necessario, aggiornare la versione.

   > [!Note]
   > Il campo della versione verrà prepopolato con la versione del componente attualmente installato, con un intervallo che si estende fino alla versione principale successiva del componente, ma non includendola.

   ![aggiungere il prerequisito roslyn](media/add-roslyn-prerequisite.png)

* Fare clic su **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aggiornare le impostazioni di Debug per il progettoUpdate Debug settings for the project

Se si desidera eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che le impostazioni di progetto per l'azione **di** > **avvio** di debug abbia il **avviato programma esterno:** valore impostato sul file *devenv.exe* dell'installazione di Visual Studio 2017.

Potrebbe essere simile a: *C: . .* . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

![avviare un programma esterno](media/start-external-program.png)

> [!Note]
> L'azione di avvio di debug viene in genere archiviata nel file *con estensione csproj.user.* Questo file è in genere incluso nel file *con estensione gitignore* e, pertanto, non viene normalmente salvato con altri file di progetto quando viene eseguito il commit nel controllo del codice sorgente. Di conseguenza, se la soluzione è stata aggiornata dal controllo del codice sorgente, è probabile che il progetto non abbia valori impostati per azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 dicono un file *con estensione csproj.user* creato con impostazioni predefinite che puntano alla directory di installazione corrente di Visual Studio. Tuttavia, se si esegue la migrazione di un'estensione VSIX v2, è probabile che il file con estensione csproj.user conterrà riferimenti alla directory di installazione della versione precedente di Visual Studio.However if you are migrating a VSIX v2 extension, it is likely that the *.csproj.user* file will contain references to the previous Visual Studio version's install directory. L'impostazione del valore per**l'azione Avvio** **debug** > consentirà l'avvio dell'istanza sperimentale di Visual Studio corretta quando si tenta di eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione viene compilata correttamente (come VSIX v3)

* Compilare il progetto VSIX.
* Decomprimere il valore VSIX generato.
  * Per impostazione predefinita, il file VSIX si trova all'interno di *bin/Debug* o *bin/Release* come *[YourCustomExtension].vsix*.
  * Rinominare *.vsix* in *.zip* per visualizzare facilmente il contenuto.
* Verificare l'esistenza di tre file:
  * *estensione.vsixmanifest*
  * *manifest.json (manifesto.*
  * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Verificare quando sono installati tutti i prerequisiti necessari

Verificare che il disco rigido virtuale viene installato correttamente in un computer in cui sono installati tutti i prerequisiti necessari.

> [!Note]
> Prima di installare qualsiasi estensione, arrestare tutte le istanze di Visual Studio.

Tentare di installare l'estensione:

* In Visual Studio 2017

![Programma di installazione VSIX in Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltativo: controllare le versioni precedenti di Visual Studio.Optional: Check on previous versions of Visual Studio.
  * Dimostra la compatibilità con le versioni precedenti.
  * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltativo: verificare che Controllo versioni programma di installazione VSIX offra una scelta di versioni diverse.
  * Include versioni precedenti di Visual Studio (se installato).
  * Include Visual Studio 2017.

Se Visual Studio è stato aperto di recente, è possibile che venga visualizzata una finestra di dialogo simile alla seguente:If Visual Studio was recently opened, you might see a dialog box like this:

![vs processi in esecuzione](media/vs-running-processes.png)

Attendere l'arresto dei processi o terminare manualmente le attività. È possibile trovare i processi in base al nome elencato o con il PID elencato tra parentesi.

> [!Note]
> Questi processi non verranno arrestati automaticamente durante l'esecuzione di un'istanza di Visual Studio.These processes will not automatically shut down while an instance of Visual Studio is running. Assicurarsi di aver arrestato tutte le istanze di Visual Studio nel computer, incluse quelle di altri utenti, quindi continuare a riprovare.

## <a name="check-when-missing-the-required-prerequisites"></a>Verificare quando mancano i prerequisiti necessariCheck when missing the required prerequisites

* Tentare di installare l'estensione in un computer con Visual Studio 2017 che NON contiene tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifichi i componenti mancanti e li elenchi come prerequisito in VSIXInstaller.
* Nota: la quota altimetrica sarà necessaria se è necessario installare i prerequisiti con l'estensione.

![prerequisito mancante di vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidere i componenti

Quando si cercano le dipendenze, si scoprirà che una dipendenza potrebbe eseguire il mapping a più componenti. Per determinare quali dipendenze è necessario specificare come prerequisito, è consigliabile scegliere un componente con una funzionalità simile all'estensione e considerare anche gli utenti e il tipo di componenti che probabilmente avrebbero installato o non sarebbe dispiacerebbe installare. Si consiglia inoltre di creare le estensioni in modo che i prerequisiti richiesti soddisfino solo il minimo che consentirà l'esecuzione dell'estensione e per funzionalità aggiuntive di essere domeggiate se alcuni componenti non vengono rilevati.

Per fornire ulteriori indicazioni, abbiamo identificato alcuni tipi di estensione comuni e i relativi prerequisiti suggeriti:

Tipo di estensione | Nome visualizzato | ID
--- | --- | ---
Editor | Editor principale di Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base Carico di lavoro desktop gestito | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger JIT | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Trovare gli URL dei componenti

L'elenco dei componenti ordinati in base al prodotto Visual Studio si trova in [Visual Studio 2017 workload and component Ids](/visualstudio/install/workload-and-component-ids?view=vs-2019). Usare questi ID componente per gli ID dei prerequisiti nel manifesto.

Se non si è certi di quale componente contenga un file binario specifico, scaricare il foglio di [calcolo di mapping Componente -> binario](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>Vs2017-ComponentBinaryMapping.xlsx

Nel foglio di Excel sono presenti quattro colonne: **Nome componente**, **IdComponente**, **Versione**e **Nomi binari/File**.  È possibile utilizzare i filtri per cercare e trovare componenti e file binari specifici.

Per tutti i riferimenti, determinare innanzitutto quali si trovano nel componente dell'editor principale (Microsoft.VisualStudio.Component.CoreEditor).  È necessario specificare almeno il componente editor principale come prerequisito per tutte le estensioni. Tra i riferimenti che vengono lasciati nell'editor principale, aggiungere filtri nella sezione **Binaries / Nomi file** per trovare i componenti che dispongono di uno qualsiasi dei sottoinsiemi di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e si sa che il progetto contiene un riferimento a *VSDebugEng.dll* e *VSDebug.dll*, fare clic sul pulsante del filtro nell'intestazione **Binaries / Nomi file.**  Cercare "VSDebugEng.dll" e selezionare *OK*.  Quindi fare clic sul pulsante di filtro nell'intestazione **Binaries / Nomi file** nuovamente e cercare "VSDebug.dll".  Selezionare la casella di controllo **Aggiungi la selezione corrente da filtrare** e selezionare **OK**.  Esaminare ora il nome del **componente** per trovare un componente più correlato al tipo di estensione. In questo esempio è necessario scegliere il debugger Just-In-Time e aggiungerlo al vsixmanifest.
* Se si è noti che il progetto si occupa di elementi del debugger, è possibile cercare "debugger" nella casella di ricerca del filtro per vedere quali componenti contengono debugger nel nome.

## <a name="specify-a-visual-studio-2017-release"></a>Specificare una versione di Visual Studio 2017Specify a Visual Studio 2017 release

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, dipende da una funzionalità rilasciata in 15.3, è necessario specificare il numero di build in VSIX **InstallationTarget**. Ad esempio, la versione 15.3 ha un numero di build di '15.0.26730.3'. È possibile visualizzare il mapping dei rilasci ai numeri di build [qui](../install/visual-studio-build-numbers-and-release-dates.md). L'utilizzo del numero di versione '15.3' non funziona correttamente.

Se l'estensione richiede 15.3 o superiore, è necessario dichiarare la **versione InstallationTarget** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
