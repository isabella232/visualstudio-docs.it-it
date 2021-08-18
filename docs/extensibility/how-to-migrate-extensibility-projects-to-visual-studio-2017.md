---
title: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017
titleSuffix: ''
description: Informazioni su come aggiornare i progetti di estendibilità a Visual Studio 2017 e su come eseguire l'aggiornamento dal manifesto dell'estensione versione 2 al manifesto VSIX versione 3.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 9e10a9061eae777728b9874c959483edfc7abe15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050338"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: Eseguire la migrazione di progetti di estendibilità Visual Studio 2017

Questo documento illustra come aggiornare i progetti di estendibilità a Visual Studio 2017. Oltre a descrivere come aggiornare i file di progetto, descrive anche come eseguire l'aggiornamento dal manifesto dell'estensione versione 2 (VSIX v2) al nuovo formato di manifesto VSIX versione 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installare Visual Studio 2017 con i carichi di lavoro necessari

Assicurarsi che l'installazione includa i carichi di lavoro seguenti:

* Sviluppo per desktop .NET
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire la soluzione VSIX in Visual Studio 2017

Per tutti i progetti VSIX sarà necessario un aggiornamento unidiredato della versione principale a Visual Studio 2017.

Il file di progetto (ad esempio **con estensione csproj*) verrà aggiornato:

* MinimumVisualStudioVersion: ora impostato su 15.0
* OldToolsVersion (se esistente in precedenza): ora impostata su 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto di NuGet Microsoft.VSSDK.BuildTools

> [!Note]
> Se la soluzione non fa riferimento al pacchetto di NuGet Microsoft.VSSDK.BuildTools, è possibile ignorare questo passaggio.

Per compilare l'estensione nel nuovo formato VSIX v3 (versione 3), la soluzione dovrà essere compilata con i nuovi strumenti di compilazione VSSDK. Verrà installato con Visual Studio 2017, ma l'estensione VSIX v2 potrebbe contenere un riferimento a una versione precedente tramite NuGet. In questo caso, è necessario installare manualmente un aggiornamento del pacchetto di NuGet Microsoft.VSSDK.BuildTools per la soluzione.

Per aggiornare i NuGet a Microsoft.VSSDK.BuildTools:

* Fare clic con il pulsante destro del mouse sulla soluzione **e scegliere Gestisci NuGet pacchetti per la soluzione**.
* Passare alla **scheda** Aggiornamenti.
* Selezionare **Microsoft.VSSDK.BuildTools (versione più recente).**
* Premere **Aggiorna**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportare modifiche al manifesto dell'estensione VSIX

Per assicurarsi che l'installazione di Visual Studio dell'utente abbia tutti gli assembly necessari per eseguire l'estensione, specificare tutti i componenti o i pacchetti prerequisiti nel file manifesto dell'estensione. Quando un utente tenta di installare l'estensione, VSIXInstaller verifica se sono installati tutti i prerequisiti. Se alcuni sono mancanti, all'utente verrà richiesto di installare i componenti mancanti come parte del processo di installazione dell'estensione.

> [!Note]
> Come minimo, tutte le estensioni devono specificare il Visual Studio principale dell'editor come prerequisito.

* Modificare il file manifesto dell'estensione (in *genere denominato source.extension.vsixmanifest).*
* Assicurarsi `InstallationTarget` che includa la versione 15.0.
* Aggiungere i prerequisiti di installazione necessari (come illustrato nell'esempio seguente).
  * È consigliabile specificare solo gli ID componente per i prerequisiti di installazione.
  * Per istruzioni sull'identificazione degli ID dei componenti, vedere la sezione [alla fine di questo documento.](#find-component-ids)

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opzione: usare la finestra di progettazione per apportare modifiche al manifesto dell'estensione VSIX

Anziché modificare direttamente il file XML del  manifesto, è possibile usare la nuova scheda Prerequisiti in Progettazione manifesto per selezionare i prerequisiti e il codice XML verrà aggiornato automaticamente.

> [!Note]
> Progettazione manifesto consentirà solo di selezionare componenti (non carichi di lavoro o pacchetti) installati nell'istanza Visual Studio corrente. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente non attualmente installato, modificare direttamente il file XML del manifesto.

* Aprire il file *source.extension.vsixmanifest [Design].*
* Selezionare **la scheda Prerequisiti** e fare clic sul **pulsante** Nuovo.

   ![Finestra di progettazione del manifesto VSIX](media/vsix-manifest-designer.png)

* Verrà **visualizzata la finestra Aggiungi** nuovo prerequisito.

   ![aggiungere il prerequisito vsix](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a **discesa Nome** e selezionare il prerequisito desiderato.
* Se necessario, aggiornare la versione.

   > [!Note]
   > Il campo della versione verrà precompilato con la versione del componente attualmente installato, con un intervallo che si estende fino alla versione principale successiva del componente, ma non inclusa.

   ![aggiungere il prerequisito roslyn](media/add-roslyn-prerequisite.png)

* Fare clic su **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aggiornare le impostazioni di debug per il progetto

Se si vuole eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che per le impostazioni del progetto per l'azione Avvia debug il valore Avvia programma esterno: sia impostato sul filedevenv.exedell'installazione  >   di Visual Studio 2017.  

Potrebbe essere simile a: *C:\Programmi (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![avviare un programma esterno](media/start-external-program.png)

> [!Note]
> L'azione di avvio del debug viene in genere archiviata nel file *con estensione csproj.user.* Questo file è in genere incluso nel file con estensione *gitignore* e, pertanto, in genere non viene salvato con altri file di progetto quando viene eseguito il commit nel controllo del codice sorgente. Di conseguenza, se la soluzione è stata appena estratta dal controllo del codice sorgente, è probabile che per il progetto non siano impostati valori per l'azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 avranno un file con estensione *csproj.user* creato con i valori predefiniti che puntano alla directory Visual Studio di installazione corrente. Tuttavia, se si esegue la migrazione di un'estensione VSIX v2, è probabile che il file con estensione *csproj.user* conterrà riferimenti alla directory di installazione della versione Visual Studio precedente. L'impostazione del valore per **l'azione** Avvia debug consentirà l'avvio Visual Studio'istanza sperimentale corretta quando  >   si tenta di eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione venga compilata correttamente (come VSIX v3)

* Compilare il progetto VSIX.
* Decomprimere il file VSIX generato.
  * Per impostazione predefinita, il file VSIX si trova all'interno *di bin/Debug* o *bin/Release* *come [YourCustomExtension].vsix*.
  * Rinominare *.vsix in* *.zip* per visualizzare facilmente il contenuto.
* Verificare l'esistenza di tre file:
  * *extension.vsixmanifest*
  * *manifest.jssu*
  * *catalog.jssu*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Controllare quando sono installati tutti i prerequisiti necessari

Verificare che VSIX sia installato correttamente in un computer in cui sono installati tutti i prerequisiti necessari.

> [!Note]
> Prima di installare qualsiasi estensione, arrestare tutte le istanze di Visual Studio.

Provare a installare l'estensione:

* A Visual Studio 2017

![Programma di installazione VSIX Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltativo: controllare le versioni precedenti di Visual Studio.
  * Dimostra la compatibilità con le versioni precedenti.
  * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltativo: verificare che il controllo della versione del programma di installazione VSIX offra una scelta di versioni.
  * Include le versioni precedenti di Visual Studio (se installate).
  * Include Visual Studio 2017.

Se Visual Studio è stata aperta di recente, potrebbe essere visualizzata una finestra di dialogo simile alla seguente:

![processi in esecuzione](media/vs-running-processes.png)

Attendere l'arresto dei processi o terminare manualmente le attività. È possibile trovare i processi in base al nome elencato o con il PID elencato tra parentesi.

> [!Note]
> Questi processi non verranno arrestati automaticamente durante l'esecuzione Visual Studio'istanza di . Assicurarsi di aver arrestato tutte le istanze di Visual Studio nel computer, incluse quelle di altri utenti, quindi continuare a riprovare.

## <a name="check-when-missing-the-required-prerequisites"></a>Controllare se mancano i prerequisiti necessari

* Provare a installare l'estensione in un computer con Visual Studio 2017 che NON CONTIENE tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifichi i componenti mancanti e li elenchi come prerequisito in VSIXInstaller.
* Nota: l'elevazione dei privilegi sarà necessaria se è necessario installare i prerequisiti con l'estensione.

![vsixinstaller missing prerequisite (Prerequisito mancante per vsixinstaller)](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidere i componenti

Quando si cercano le dipendenze, si scoprirà che è possibile eseguire il mapping di una dipendenza a più componenti. Per determinare quali dipendenze è necessario specificare come prerequisito, è consigliabile scegliere un componente con una funzionalità simile all'estensione e prendere in considerazione anche gli utenti e il tipo di componenti che probabilmente avrebbe installato o che non sarebbe importante installare. È anche consigliabile compilare le estensioni in modo che i prerequisiti richiesti soddisfino solo il requisito minimo che consentirà l'esecuzione dell'estensione e, per le funzionalità aggiuntive, che siano inattive se non vengono rilevati determinati componenti.

Per fornire altre indicazioni, sono stati identificati alcuni tipi di estensione comuni e i relativi prerequisiti consigliati:

Tipo di estensione | Nome visualizzato | ID
--- | --- | ---
Editor | Editor principale di Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base Carico di lavoro desktop gestito | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger JIT | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Trovare gli ID dei componenti

L'elenco dei componenti ordinati in base Visual Studio prodotto si trova Visual Studio [2017](../install/workload-and-component-ids.md?view=vs-2019&preserve-view=true)e id componente . Usare questi ID componente per gli ID dei prerequisiti nel manifesto.

Se non si è certi del componente che contiene un file binario specifico, scaricare il foglio di [calcolo Del mapping binario component ->](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Sono presenti quattro colonne nel foglio Excel: **Nome** componente, **ComponentId,** **Versione** e **Nomi file/binari.**  È possibile usare i filtri per cercare e trovare componenti e file binari specifici.

Per tutti i riferimenti, determinare innanzitutto quali sono nel componente dell'editor principale (Microsoft.VisualStudio.Component.CoreEditor).  Come minimo, è necessario che il componente dell'editor principale sia specificato come prerequisito per tutte le estensioni. Tra i riferimenti rimasti non presenti nell'editor principale, aggiungere filtri nella sezione **Nomi file/file** binari per trovare i componenti che dispongono di uno dei subset di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e si sa che il progetto ha un riferimento a *VSDebugEng.dll* *eVSDebug.dll*, fare clic sul pulsante filtro nell'intestazione **Binari/Nomi** file.  Cercare "VSDebugEng.dll" e selezionare *OK.*  Fare quindi di nuovo clic sul pulsante filtro **nell'intestazione Binari/Nomi** file e cercare "VSDebug.dll".  Selezionare la casella **di controllo Aggiungi selezione corrente per filtrare** e selezionare **OK.**  Esaminare ora Il nome **del componente per** trovare un componente più correlato al tipo di estensione. In questo esempio si sceglie il debugger JUST-In-Time e lo si aggiunge al vsixmanifest.
* Se si sa che il progetto gestisce gli elementi del debugger, è possibile cercare "debugger" nella casella di ricerca dei filtri per vedere quali componenti contengono il debugger nel nome.

## <a name="specify-a-visual-studio-2017-release"></a>Specificare una versione Visual Studio 2017

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, dipende da una funzionalità rilasciata nella versione 15.3, è necessario specificare il numero di build in VSIX **InstallationTarget.** Ad esempio, la versione 15.3 ha un numero di build "15.0.26730.3". È possibile visualizzare il mapping delle versioni ai numeri di build [qui.](../install/visual-studio-build-numbers-and-release-dates.md) L'uso del numero di versione "15.3" non funzionerà correttamente.

Se l'estensione richiede la versione 15.3 o successiva, è necessario dichiarare **InstallationTarget Version** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```