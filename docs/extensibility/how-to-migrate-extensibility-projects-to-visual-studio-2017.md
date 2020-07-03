---
title: 'Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 37f7259c1133ea51e004b5f6b2061427ff71dea0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905849"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: eseguire la migrazione di progetti di estendibilità a Visual Studio 2017

Questo documento illustra come aggiornare i progetti di estensibilità a Visual Studio 2017. Oltre a descrivere come aggiornare i file di progetto, viene descritto anche come eseguire l'aggiornamento da estensione manifest versione 2 (VSIX v2) al nuovo formato del manifesto VSIX versione 3 (VSIX V3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Installare Visual Studio 2017 con i carichi di lavoro necessari

Assicurarsi che l'installazione includa i carichi di lavoro seguenti:

* Sviluppo per desktop .NET
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire la soluzione VSIX in Visual Studio 2017

Per tutti i progetti VSIX è necessario eseguire l'aggiornamento unidirezionale di una versione principale a Visual Studio 2017.

Il file di progetto (ad esempio **. csproj*) verrà aggiornato:

* MinimumVisualStudioVersion-ora impostato su 15,0
* OldToolsVersion (se esiste già)-ora impostato su 14,0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto NuGet Microsoft. VSSDK. BuildTools

> [!Note]
> Se la soluzione non fa riferimento al pacchetto NuGet Microsoft. VSSDK. BuildTools, è possibile ignorare questo passaggio.

Per creare l'estensione nel nuovo formato VSIX V3 (versione 3), la soluzione deve essere compilata con i nuovi strumenti di compilazione VSSDK. Questa operazione verrà installata con Visual Studio 2017, ma l'estensione VSIX V2 potrebbe contenere un riferimento a una versione precedente tramite NuGet. In tal caso, sarà necessario installare manualmente un aggiornamento del pacchetto NuGet Microsoft. VSSDK. BuildTools per la soluzione.

Per aggiornare i riferimenti NuGet a Microsoft. VSSDK. BuildTools:

* Fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet per la soluzione**.
* Passare alla scheda **aggiornamenti** .
* Selezionare **Microsoft. VSSDK. BuildTools (versione più recente)**.
* Premere **Aggiorna**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Modificare il manifesto dell'estensione VSIX

Per assicurarsi che l'installazione dell'utente di Visual Studio includa tutti gli assembly necessari per eseguire l'estensione, specificare tutti i componenti o i pacchetti dei prerequisiti nel file manifesto dell'estensione. Quando un utente tenta di installare l'estensione, VSIX Installer verificherà se sono installati tutti i prerequisiti. Se alcune sono mancanti, all'utente verrà richiesto di installare i componenti mancanti come parte del processo di installazione dell'estensione.

> [!Note]
> Come prerequisito, tutte le estensioni devono specificare almeno il componente dell'editor principale di Visual Studio.

* Modificare il file manifesto dell'estensione, in genere denominato *source. Extension. vsixmanifest*.
* Verificare che `InstallationTarget` includa 15,0.
* Aggiungere i prerequisiti di installazione necessari, come illustrato nell'esempio riportato di seguito.
  * È consigliabile specificare solo gli ID componente per i prerequisiti di installazione.
  * Per [istruzioni sull'identificazione degli ID dei componenti](#find-component-ids), vedere la sezione alla fine di questo documento.

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

Anziché modificare direttamente il file XML del manifesto, è possibile usare la scheda nuovi **prerequisiti** in Progettazione manifesto per selezionare i prerequisiti e il codice XML verrà aggiornato.

> [!Note]
> La finestra di progettazione del manifesto consente solo di selezionare i componenti (non i carichi di lavoro o i pacchetti) installati nell'istanza corrente di Visual Studio. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente che non è attualmente installato, modificare direttamente il file XML del manifesto.

* File Open *source. Extension. vsixmanifest [Progettazione]* .
* Selezionare la scheda **prerequisiti** e premere il pulsante **nuovo** .

   ![Progettazione manifesto VSIX](media/vsix-manifest-designer.png)

* Viene visualizzata la finestra **Aggiungi nuovo prerequisito** .

   ![Aggiungi prerequisito VSIX](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a discesa per **nome** e selezionare il prerequisito desiderato.
* Se necessario, aggiornare la versione.

   > [!Note]
   > Il campo della versione verrà pre-popolato con la versione del componente attualmente installato, con un intervallo che si estende fino a (senza includere) la versione principale successiva del componente.

   ![Aggiungi prerequisito Roslyn](media/add-roslyn-prerequisite.png)

* Fare clic su **OK**.

## <a name="update-debug-settings-for-the-project"></a>Aggiornare le impostazioni di debug per il progetto

Se si vuole eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che l'azione impostazioni progetto per **debug**di  >  **avvio** disponga del **programma avvia esterno:** valore impostato sul file di *devenv.exe* dell'installazione di Visual Studio 2017.

Il file potrebbe essere simile a: *c:\Programmi (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![Avvia programma esterno](media/start-external-program.png)

> [!Note]
> L'azione di avvio del debug viene in genere archiviata nel file con *estensione csproj. User* . Questo file è generalmente incluso nel file con *estensione gitignore* e, di conseguenza, non viene salvato normalmente con altri file di progetto quando ne viene eseguito il commit nel controllo del codice sorgente. Di conseguenza, se la soluzione è stata eliminata dal controllo del codice sorgente, è probabile che per il progetto non siano impostati valori per l'azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 avranno un file con *estensione csproj. User* creato con i valori predefiniti che puntano alla directory di installazione di Visual Studio corrente. Tuttavia, se si esegue la migrazione di un'estensione VSIX V2, è probabile che il file *. csproj. User* conterrà riferimenti alla directory di installazione precedente della versione di Visual Studio. Impostando il valore per l'azione di avvio del **debug**  >  **Start action** , sarà possibile avviare l'istanza sperimentale di Visual Studio corretta quando si tenta di eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione venga compilata correttamente (come VSIX V3)

* Compilare il progetto VSIX.
* Decomprimere il progetto VSIX generato.
  * Per impostazione predefinita, il file VSIX si trova all'interno di *bin/debug* o *bin/Release* come *[YourCustomExtension]. vsix*.
  * Rinominare *. vsix* in *. zip* per visualizzare facilmente il contenuto.
* Verificare la presenza di tre file:
  * *estensione. vsixmanifest*
  * *manifest.js*
  * *catalog.js*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Verificare quando sono installati tutti i prerequisiti necessari

Verificare che VSIX venga installato correttamente in un computer in cui sono installati tutti i prerequisiti necessari.

> [!Note]
> Prima di installare un'estensione, arrestare tutte le istanze di Visual Studio.

Tentativo di installare l'estensione:

* In Visual Studio 2017

![Programma di installazione VSIX in Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltativo: controllare le versioni precedenti di Visual Studio.
  * Prova la compatibilità con le versioni precedenti.
  * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltativo: verificare che il controllo della versione del programma di installazione VSIX offra una scelta di versioni.
  * Include le versioni precedenti di Visual Studio (se installate).
  * Include Visual Studio 2017.

Se Visual Studio è stato aperto di recente, è possibile che venga visualizzata una finestra di dialogo simile alla seguente:

![processi di Visual Studio in esecuzione](media/vs-running-processes.png)

Attendere che i processi vengano arrestati o terminare manualmente le attività. È possibile trovare i processi in base al nome elencato o con il PID elencato tra parentesi.

> [!Note]
> Questi processi non vengono arrestati automaticamente mentre un'istanza di Visual Studio è in esecuzione. Assicurarsi di aver arrestato tutte le istanze di Visual Studio nel computer, incluse quelle di altri utenti, quindi continuare a riprovare.

## <a name="check-when-missing-the-required-prerequisites"></a>Verifica quando mancano i prerequisiti richiesti

* Tentare di installare l'estensione in un computer con Visual Studio 2017 che non contiene tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifichi il componente o i componenti mancanti e li elenchi come prerequisito in VSIX Installer.
* Nota: l'elevazione dei privilegi sarà obbligatoria se è necessario installare i prerequisiti con l'estensione.

![prerequisito mancante VSIX Installer](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decidere i componenti

Quando si cercano le dipendenze, si noterà che una dipendenza può essere mappata a più componenti. Per determinare le dipendenze da specificare come prerequisito, è consigliabile scegliere un componente con una funzionalità simile a quella dell'estensione e prendere in considerazione anche gli utenti e il tipo di componenti che probabilmente hanno installato o che non si preoccupano di installare. È inoltre consigliabile creare le estensioni in modo che i prerequisiti richiesti soddisfino solo il minimo che consentirà l'esecuzione dell'estensione e per le funzionalità aggiuntive, se non vengono rilevati alcuni componenti.

Per fornire ulteriori indicazioni, sono stati identificati alcuni tipi di estensioni comuni e i relativi prerequisiti consigliati:

Tipo di estensione | Nome visualizzato | ID
--- | --- | ---
Editor | Editor principale di Visual Studio | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base Carico di lavoro desktop gestito | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger JIT | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Trova ID componente

L'elenco dei componenti ordinati per prodotto Visual Studio si trova in ID del carico di lavoro e dei componenti di [Visual studio 2017](/visualstudio/install/workload-and-component-ids?view=vs-2019). Usare questi ID di componenti per gli ID dei prerequisiti nel manifesto.

Se non si è certi di quale componente contenga un file binario specifico, scaricare il [foglio di calcolo di mapping binario > componente](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Il foglio di Excel contiene quattro colonne: **nome del componente**, **ComponentID**, **versione**e **nomi file/binari**.  È possibile utilizzare i filtri per cercare e individuare componenti e file binari specifici.

Per tutti i riferimenti, determinare innanzitutto quelli presenti nel componente principale dell'editor (Microsoft. VisualStudio. Component. CoreEditor).  È necessario specificare almeno il componente dell'editor principale come prerequisito per tutte le estensioni. Dei riferimenti rimasti che non sono presenti nell'editor principale, aggiungere i filtri nella sezione **file binari/file** per trovare i componenti che includono uno dei subset di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e si sa che il progetto contiene un riferimento a *VSDebugEng.dll* e *VSDebug.dll*, fare clic sul pulsante filtro nell'intestazione **file binari/file** .  Cercare "VSDebugEng.dll" e fare clic su *OK*.  Fare quindi clic sul pulsante filtro nell'intestazione file **binari/file** e cercare "VSDebug.dll".  Selezionare la casella **di controllo Aggiungi selezione corrente per filtrare** e selezionare **OK**.  Esaminare ora il **nome del componente** per trovare un componente più correlato al tipo di estensione. In questo esempio si sceglie il debugger JIT e lo si aggiunge a vsixmanifest.
* Se si è certi che il progetto occupi gli elementi del debugger, è possibile cercare "debugger" nella casella di ricerca del filtro per vedere quali componenti contengono il debugger nel nome.

## <a name="specify-a-visual-studio-2017-release"></a>Specificare una versione di Visual Studio 2017

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio dipende da una funzionalità rilasciata in 15,3, è necessario specificare il numero di build nel **installazione**VSIX. Ad esempio, la versione 15,3 include un numero di build pari a' 15.0.26730.3'. È possibile visualizzare il mapping delle versioni per compilare i numeri [qui](../install/visual-studio-build-numbers-and-release-dates.md). L'uso del numero di versione ' 15,3' non funzionerà correttamente.

Se l'estensione richiede 15,3 o versione successiva, dichiarare la **versione di installazione** come [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
