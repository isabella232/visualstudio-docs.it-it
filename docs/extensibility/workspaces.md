---
title: Aree di lavoro in Visual Studio | Microsoft Docs
description: Informazioni su come Visual Studio usa un'area di lavoro per rappresentare una raccolta di file in una cartella aperta, inclusi i provider e i servizi dell'area di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1ed660a5f52aba548d087b28f7caea4d1966fe45
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876948"
---
# <a name="workspaces"></a>Aree di lavoro

Un'area di lavoro è il modo in cui Visual Studio rappresenta qualsiasi raccolta di file in una [cartella aperta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ed è rappresentata dal <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Di per sé, l'area di lavoro non comprende il contenuto o le funzionalità correlate ai file all'interno della cartella. Fornisce invece un set generale di API per le funzionalità e le estensioni per produrre e utilizzare dati su cui altri utenti possono agire. I produttori sono composti tramite il [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) utilizzando vari attributi di esportazione.

## <a name="workspace-providers-and-services"></a>Servizi e provider dell'area di lavoro

I provider e i servizi dell'area di lavoro forniscono i dati e le funzionalità per rispondere al contenuto di un'area di lavoro. Potrebbero fornire informazioni contestuali sui file, simboli nei file di origine o funzionalità di compilazione.

Entrambi i concetti usano un [modello di Factory](https://en.wikipedia.org/wiki/Factory_method_pattern) e vengono importati tramite MEF dall'area di lavoro. Tutti gli attributi di esportazione implementano `IProviderMetadataBase` o `IWorkspaceServiceFactoryMetadata` , ma esistono tipi concreti che le estensioni devono usare per i tipi esportati.

Una differenza tra i provider e i servizi è la relazione con l'area di lavoro. Un'area di lavoro può avere molti provider di un determinato tipo, ma viene creato solo un servizio di un determinato tipo per area di lavoro. Ad esempio, un'area di lavoro dispone di molti provider di scanner di file, ma l'area di lavoro dispone di un solo servizio di indicizzazione per area

Un'altra differenza principale riguarda l'utilizzo di dati da provider e servizi. L'area di lavoro è il punto di ingresso per ottenere i dati dai provider per un paio di motivi. Per prima cosa, i provider hanno in genere un set limitato di dati creati. I dati possono essere simboli per un file di origine C# o per contesti di file di compilazione per un file di _CMakeLists.txt_ . L'area di lavoro troverà una corrispondenza tra la richiesta di un utente e i provider i cui metadati si allineano alla richiesta. In secondo luogo, alcuni scenari consentono a molti provider di contribuire a una richiesta, mentre altri scenari utilizzano il provider con la massima priorità.

Le estensioni possono invece ottenere istanze di e interagire direttamente con i servizi dell'area di lavoro. I metodi di estensione in `IWorkspace` sono disponibili per i servizi forniti da Visual Studio, ad esempio <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . L'estensione può offrire un servizio dell'area di lavoro per i componenti all'interno dell'estensione o per le altre estensioni da utilizzare. I consumer devono usare <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> o un metodo di estensione fornito nel `IWorkspace` tipo.

>[!WARNING]
> Non creare servizi in conflitto con Visual Studio. Può causare problemi imprevisti.

## <a name="disposal-on-workspace-closure"></a>Eliminazione nella chiusura dell'area di lavoro

Alla chiusura di un'area di lavoro, potrebbe essere necessario eliminare i dispositivi Extender, ma chiamare codice asincrono. L' <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interfaccia è disponibile per facilitare la scrittura di questo codice.

## <a name="related-types"></a>Tipi correlati

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> è l'entità centrale per un'area di lavoro aperta come una cartella aperta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Crea un provider per area di lavoro di cui viene creata un'istanza.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Crea un servizio per area di lavoro di cui viene creata un'istanza.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> deve essere implementato su provider e servizi che devono eseguire codice asincrono durante l'eliminazione.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornisce metodi di supporto per l'accesso a servizi noti o a servizi arbitrari.

## <a name="workspace-settings"></a>Impostazioni dell'area di lavoro

Le aree di lavoro hanno un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servizio con un controllo semplice ma potente su un'area di lavoro. Per una panoramica delle impostazioni di base, vedere [personalizzare le attività di compilazione e debug](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Le impostazioni per la maggior parte dei `SettingsType` tipi sono file con _estensione JSON_ , ad esempio _VSWorkspaceSettings.json_ e _tasks.vs.json_.

La potenza delle impostazioni dell'area di lavoro si centra intorno agli "ambiti", che sono semplicemente percorsi all'interno dell'area di lavoro. Quando un consumer chiama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> , vengono aggregati tutti gli ambiti che includono il percorso e il tipo di impostazione richiesti. La priorità di aggregazione dell'ambito è la seguente:

1. "Impostazioni locali", che corrisponde in genere alla directory della radice dell'area di lavoro `.vs` .
1. Percorso richiesto.
1. La directory padre del percorso richiesto.
1. Tutte le altre directory padre fino a includere la radice dell'area di lavoro.
1. "Impostazioni globali", che si trova in una directory utente.

Il risultato è un'istanza di <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Questo oggetto include le impostazioni per un determinato tipo e può essere sottoposto a query per l'impostazione dei nomi di chiave archiviati come `string` . I metodi <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> e i <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> metodi di estensione prevedono che il chiamante conosca il tipo del valore dell'impostazione richiesto. Poiché la maggior parte dei file di impostazioni viene salvata in modo permanente come file con _estensione JSON_ , molte chiamate utilizzeranno `string` `bool` `int` le matrici,, e di tali tipi. Sono supportati anche i tipi di oggetto. In questi casi, è possibile usare `IWorkspaceSettings` se stesso come argomento di tipo. Esempio:

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

Supponendo che queste impostazioni si trovino in un _VSWorkspaceSettings.js_ utente, i dati sono accessibili come:

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>Queste API delle impostazioni non sono correlate alle API disponibili nello `Microsoft.VisualStudio.Settings` spazio dei nomi. Le impostazioni dell'area di lavoro sono indipendenti dall'host e utilizzano i file di impostazioni specifiche dell'area di lavoro o i provider di impostazioni dinamiche.

### <a name="providing-dynamic-settings"></a>Specifica delle impostazioni dinamiche

Le estensioni possono fornire <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . Questi provider in memoria consentono alle estensioni di aggiungere impostazioni o di eseguire l'override di altri.

L'esportazione di un oggetto `IWorkspaceSettingsProvider` è diversa rispetto ad altri provider dell'area di lavoro. La factory non è `IWorkspaceProviderFactory` e non esiste alcun tipo di attributo speciale. Implementare <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> e usare invece `[Export(typeof(IWorkspaceSettingsProviderFactory))]` .

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>Quando si implementano metodi che restituiscono `IWorkspaceSettingsSource` (like `IWorkspaceSettingsProvider.GetSingleSettings` ), viene restituita un'istanza di `IWorkspaceSettings` anziché di `IWorkspaceSettingsSource` . `IWorkspaceSettings` fornisce ulteriori informazioni che possono essere utili durante alcune aggregazioni delle impostazioni.

### <a name="settings-related-apis"></a>API correlate alle impostazioni

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> legge e aggrega le impostazioni per l'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ottiene l'oggetto `IWorkspaceSettingsManager` per un'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ottiene le impostazioni per un ambito specificato aggregate in tutti gli ambiti sovrapposti.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene le impostazioni per un ambito specifico.

## <a name="workspace-suggested-practices"></a>Procedure consigliate per l'area di lavoro

- Restituire oggetti da `IWorkspaceProviderFactory.CreateProvider` o API simili che ricordano il `Workspace` contesto al momento della creazione. Le interfacce provider sono scritte in attesa che questo oggetto venga mantenuto al momento della creazione.
- Salvare le impostazioni o le cache specifiche dell'area di lavoro nel percorso "impostazioni locali" dell'area di lavoro. Creare un percorso per il file usando `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017 versione 15,6 o successiva. Per le versioni precedenti alla versione 15,6, usare il frammento di codice seguente:

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>Eventi della soluzione e caricamento automatico del pacchetto

I pacchetti caricati possono implementare `IVsSolutionEvents7` e richiamare `IVsSolution.AdviseSolutionEvents` . Include eventi di apertura e chiusura di una cartella in Visual Studio.

Un contesto dell'interfaccia utente può essere utilizzato per caricare automaticamente il pacchetto. Il valore è `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Il pacchetto SourceExplorerPackage non è stato caricato correttamente

L'estendibilità dell'area di lavoro è molto basata su MEF e gli errori di composizione causeranno il mancato caricamento del pacchetto che ospita la cartella di apertura. Se, ad esempio, un'estensione Esporta un tipo con `ExportFileContextProviderAttribute` , ma il tipo implementa solo `IWorkspaceProviderFactory<IFileContextActionProvider>` , si verificherà un errore quando si tenta di aprire una cartella in Visual Studio.

::: moniker range="vs-2017"

I dettagli dell'errore sono reperibili in _%localappdata%\microsoft\visualstudio\ 15.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Risolvere gli eventuali errori per i tipi implementati dall'estensione.

::: moniker-end

::: moniker range=">=vs-2019"

I dettagli dell'errore sono reperibili in _%localappdata%\microsoft\visualstudio\ 16.0_Id \componentmodelcache\microsoft.VisualStudio.default.err_. Risolvere gli eventuali errori per i tipi implementati dall'estensione.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

* [Contesti di file](workspace-file-contexts.md) : i provider di contesto file portano l'intelligence del codice per le aree di lavoro Apri cartella.
* [Indicizzazione](workspace-indexing.md) : l'indicizzazione dell'area di lavoro raccoglie e rende permanente le informazioni sull'area di lavoro.
