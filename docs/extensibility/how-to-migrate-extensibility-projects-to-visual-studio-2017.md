---
title: 'Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3d55055734233a385f4a6d24f8925af2f0829fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863655"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017

Questo documento illustra come aggiornare i progetti di estendibilità in Visual Studio 2017. Oltre a descrivere la procedura per aggiornare i file di progetto, la descrive anche come eseguire l'aggiornamento dalla versione del manifesto di estensione 2 (VSIX v2) per il nuova versione 3 formato del manifesto VSIX (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installare Visual Studio 2017 con carichi di lavoro necessarie

Verificare che l'installazione include i carichi di lavoro seguenti:

* Sviluppo per desktop .NET
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire una soluzione VSIX in Visual Studio 2017

Tutti i progetti VSIX richiederanno un aggiornamento unidirezionale di versione principale di Visual Studio 2017.

Il file di progetto (ad esempio **file con estensione csproj*) verranno aggiornate:

* MinimumVisualStudioVersion - è ora impostato su 15.0
* OldToolsVersion (se è presente in precedenza)-ora impostato su 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto Microsoft.VSSDK.BuildTools NuGet

> [!Note]
> Se la soluzione non fa riferimento il pacchetto Microsoft.VSSDK.BuildTools NuGet, è possibile ignorare questo passaggio.

Per compilare l'estensione nel nuovo VSIX v3 formato (versione 3), la soluzione dovrà essere compilato con i nuovi strumenti di compilazione di VSSDK. Verrà installata con Visual Studio 2017, ma l'estensione VSIX v2 potrebbe essere che contiene un riferimento a una versione precedente tramite NuGet. In questo caso, è necessario installare manualmente un aggiornamento del pacchetto Microsoft.VSSDK.BuildTools NuGet per la soluzione.

Per aggiornare i riferimenti NuGet a Microsoft.VSSDK.BuildTools:

* Pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet per la soluzione**.
* Passare il **aggiornamenti** scheda.
* Selezionare **Microsoft.VSSDK.BuildTools (versione più recente)**.
* Premere **Update**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportare modifiche al manifesto dell'estensione VSIX

Per assicurarsi che l'installazione dell'utente di Visual Studio ha tutti gli assembly necessari per eseguire l'estensione, specificare tutti i componenti dei prerequisiti o i pacchetti nel file manifesto di estensione. Quando un utente prova a installare l'estensione, il VSIX Installer controllerà se tutti i prerequisiti verranno installati. Se mancano alcuni, l'utente verrà chiesto di installare i componenti mancanti come parte del processo di installazione di estensione.

> [!Note]
> Come minimo, tutte le estensioni è necessario specificare il componente editor principale di Visual Studio come prerequisito.

* Modificare il file manifesto di estensione (in genere chiamati *vsixmanifest*).
* Assicurarsi che `InstallationTarget` include 15.0.
* Aggiungere i prerequisiti di installazione richiesti (come illustrato nell'esempio seguente).
   * È consigliabile che specificare solo ID di componenti dei prerequisiti.
   * Vedere la sezione alla fine di questo documento anche per [istruzioni per identificare gli ID componente](#find-component-ids).

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opzione: Usare la finestra di progettazione per apportare modifiche al manifesto dell'estensione VSIX

Anziché modificare direttamente il file XML del manifesto, è possibile usare il nuovo **prerequisiti** scheda della finestra di progettazione manifesto per selezionare i prerequisiti e il valore XML verrà aggiornato automaticamente.

> [!Note]
> La finestra Progettazione manifesto solo consentono di selezionare i componenti (non i carichi di lavoro o pacchetti) e che siano installati nell'istanza di Visual Studio corrente. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente che non è attualmente installato, è possibile modificare direttamente il manifesto XML.

* Aprire *vsixmanifest [Progettazione]* file.
* Selezionare **prerequisiti** scheda e premere **New** pulsante.

   ![Progettazione manifesto VSIX](media/vsix-manifest-designer.png)

* Il **Aggiungi nuovo prerequisito** aprirà la finestra.

   ![aggiungere il prerequisito di vsix](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a discesa per **nome** e selezionare il prerequisito desiderato.
* Se necessario, aggiornare la versione.

   > [!Note]
   > Il campo della versione verranno prepopolato con la versione del componente attualmente installato, con un intervallo che si estende fino a (ma non incluse) la prossima versione principale del componente.

   ![aggiungere il prerequisito di roslyn](media/add-roslyn-prerequisite.png)

* Fare clic su **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aggiornare le impostazioni di Debug per il progetto

Se si vuole eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che le impostazioni di progetto per **Debug** > **azione di avvio** ha la **avviare esterno programma:** valore impostato il *devenv.exe* file di installazione di Visual Studio 2017.

Potrebbe essere simile: *C:\Programmi\Microsoft file (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Avvia programma esterno](media/start-external-program.png)

> [!Note]
> L'azione di avvio Debug è in genere archiviato nel *. csproj* file. Questo file è in genere incluso nel *file con estensione gitignore* di file e, di conseguenza, non vengono in genere salvate con altri file di progetto quando il commit al controllo del codice sorgente. Di conseguenza, se si have effettuato il pull della soluzione aggiornata dal controllo del codice sorgente è probabile che il progetto non avrà nessun valore impostato per l'azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 avrà un *. csproj* file creato con le impostazioni predefinite che punta alla directory di installazione di Visual Studio corrente. Tuttavia se si esegue la migrazione di estensione VSIX v2, è probabile che il *. csproj* file conterrà i riferimenti a directory di installazione della versione di Visual Studio precedente. Impostazione del valore per **Debug** > **azione di avvio** consentirà l'istanza sperimentale di Visual Studio corretto da avviare quando si prova a eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione viene compilata correttamente (come un VSIX v3)

* Compilare il progetto VSIX.
* Decomprimere il pacchetto VSIX generato.
   * Per impostazione predefinita, il file VSIX si trova all'interno *bin/Debug* oppure *bin/Release* come *VSIX [YourCustomExtension]*.
   * Rinominare *VSIX* al *zip* visualizzare facilmente il contenuto.
* Verificare l'esistenza di tre file:
   * *extension.vsixmanifest*
   * *manifest.json*
   * *catalog.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Controllare quando vengono installati tutti i prerequisiti obbligatori

Verificare che il progetto VSIX viene installato correttamente in un computer con tutti i prerequisiti installati.

> [!Note]
> Prima di installare qualsiasi estensione, arrestare tutte le istanze di Visual Studio.

Tentativo di installare l'estensione:

* On Visual Studio 2017

![Programma di installazione VSIX in Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltative: Per controllare le versioni precedenti di Visual Studio.
   * Dimostri la compatibilità con le versioni precedenti.
   * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltative: Verificare che VSIX Installer versione controllo offre una vasta gamma di versioni.
   * Include le versioni precedenti di Visual Studio (se installato).
   * Include Visual Studio 2017.

Se recentemente è stato aperto Visual Studio, potrebbe essere visualizzata una finestra di dialogo simile alla seguente:

![i processi in esecuzione Visual Studio](media/vs-running-processes.png)

Attendere i processi da arrestare o terminare manualmente le attività. È possibile trovare i processi dal nome elencato o con il PID con elencato tra parentesi.

> [!Note]
> Questi processi non automaticamente arresterà durante l'esecuzione di un'istanza di Visual Studio. Assicurarsi di aver arrestare tutte le istanze di Visual Studio nel computer, comprese quelle di altri utenti, quindi continuare a ripetere.

## <a name="check-when-missing-the-required-prerequisites"></a>Controllare quando mancano i prerequisiti obbligatori

* Tenta di installare l'estensione in un computer con Visual Studio 2017 che non contengono tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifica il componente mancante/s e li elenca come prerequisito di VSIX Installer.
* Nota: L'elevazione verrà richiesto se tutti i prerequisiti necessari per l'installazione con l'estensione.

![Prerequisito mancante VSIX Installer](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidere sui componenti

Quando si cercano le dipendenze, si noterà che è stato possibile eseguire il mapping di una dipendenza da più componenti. Per determinare quali dipendenze è necessario specificare il prerequisito, è consigliabile scegliere un componente che dispone di una funzionalità simile all'estensione e considerare anche gli utenti e il tipo di componenti sarebbe probabilmente installate o non sarebbe presente l'installazione. È anche consigliabile predefiniti delle estensioni in un modo in cui i prerequisiti necessari soddisfano solo il valore minimo che consentirà l'estensione per l'esecuzione e per le funzionalità aggiuntive chiedere di essere inattivi se determinati componenti non vengono rilevati.

Per fornire ulteriori indicazioni, sono stati identificati alcuni tipi di estensione più comuni e sui relativi prerequisiti suggerite:

Tipo di estensione | Nome visualizzato | Id
--- | --- | ---
Editor | Editor principale di Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base Carico di lavoro desktop gestito | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger JIT | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Trovare gli ID componente

L'elenco dei componenti ordinati per prodotto Visual Studio si trova [gli ID di carico di lavoro e dei componenti di Visual Studio 2017](https://aka.ms/vs2017componentIDs). Utilizzare questi ID componente per l'ID dei prerequisiti nel manifesto.

Se si è certi che il componente contiene un file binario specifico, scaricare il [componenti -> del foglio di calcolo di mapping dei tipi binari](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Esistono quattro colonne nel foglio di Excel: **Nome del componente**, **ComponentId**, **versione**, e **binario / nomi File**.  È possibile usare i filtri per cercare e trovare i file binari e componenti specifici.

Per tutti i riferimenti, determinare innanzitutto quali lo sono nel componente editor (Microsoft.VisualStudio.Component.CoreEditor) core.  Come minimo, è necessario il componente editor principale per specificare come prerequisito per tutte le estensioni. I riferimenti che rimangono non inclusi nell'editor principale, aggiungere i filtri nel **i file binari / nomi di file** sezione per trovare i componenti con uno qualsiasi dei subset di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e sapere che il progetto contiene un riferimento a *Vsdebugeng* e *VSDebug.dll*, fare clic sul pulsante filtro nel **binari / nomi file**intestazione.  Cercare "Vsdebugeng" e selezionare *OK*.  Successivamente fare clic sul pulsante filtro il **i file binari / nomi di file** intestazione nuovamente e cercare "VSDebug.dll".  Selezionare la casella di controllo **aggiungere la selezione corrente da filtrare** e selezionare **OK**.  Ora esaminare il **nome del componente** per trovare un componente che risulta maggiormente correlati per il tipo dell'estensione. In questo esempio verrà scelto il Just-In-Time del debugger e aggiungerlo al vsixmanifest.
* Se si sa che il progetto gestisce gli elementi del debugger, è possibile cercare "debug" nella casella di ricerca del filtro per visualizzare quali componenti contengono debugger nel relativo nome.

## <a name="specify-a-visual-studio-2017-release"></a>Specificare una versione di Visual Studio 2017

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, dipende da una funzionalità disponibile nella versione 15.3, è necessario specificare il numero di build in VSIX **la destinazione di installazione**. Ad esempio, versione 15.3 presenta un numero di build del '15.0.26730.3'. È possibile visualizzare il mapping delle versioni per i numeri di build [qui](../install/visual-studio-build-numbers-and-release-dates.md). Utilizzando il numero di versione '15.3' non funzionerà correttamente.

Se l'estensione richiede la versione 15.3 o versioni successive, è necessario dichiarare la **versione la destinazione di installazione** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
