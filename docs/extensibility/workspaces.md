---
title: Le aree di lavoro in Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: da61f3f46d9737bef6c14cf69a52be1951da28fb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55925436"
---
# <a name="workspaces"></a>Workspaces

Un'area di lavoro è come Visual Studio rappresenta qualsiasi raccolta di file nel [Apri cartella](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), e viene rappresentato dal <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo. Di per sé l'area di lavoro non comprende il contenuto o le funzionalità relative ai file all'interno della cartella. Piuttosto, fornisce un set generale di API per le funzionalità e le estensioni per produrre e utilizzare dati che altri utenti possono essere eseguite. I producer sono composti da tramite il [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) utilizzando vari esporti gli attributi.

## <a name="workspace-providers-and-services"></a>Provider dell'area di lavoro e servizi

Servizi e i provider dell'area di lavoro forniscono i dati e le funzionalità per ricevere il contenuto di un'area di lavoro. Potrebbero fornire informazioni sul file contestuale, i simboli nel file di origine, o la funzionalità di compilazione.

Entrambi i concetti di usare una [modello factory](https://en.wikipedia.org/wiki/Factory_method_pattern) e importati tramite MEF nell'area di lavoro. Implementano tutti gli attributi di esportazione `IProviderMetadataBase` o `IWorkspaceServiceFactoryMetadata`, ma esistono tipi concreti utilizzate dalle estensioni per i tipi esportati.

Una differenza tra provider e i servizi è la loro relazione con l'area di lavoro. Un'area di lavoro può avere molti provider di un determinato tipo, ma solo un servizio di un particolare tipo viene creato per ogni area di lavoro. Ad esempio, un'area di lavoro ha molti provider di analisi di file ma l'area di lavoro ha un solo servizio di indicizzazione per ogni area di lavoro.

Un'altra differenza principale è il consumo dei dati dal provider e i servizi. L'area di lavoro è il punto di ingresso per ottenere dati dai provider per due motivi. In primo luogo, i provider hanno in genere alcuni set ristretto di dati creati. I dati possono essere i simboli per un C# file di origine o contesti di file per compilare un _cmakelists. txt_ file. L'area di lavoro corrisponderanno richiesta del consumer ai provider i cui metadati allineare con la richiesta. In secondo luogo, consentano di alcuni scenari per molti provider di contribuire a una richiesta mentre altri scenari di usare il provider con priorità più alta.

Al contrario, le estensioni possono ottenere istanze di e interagire direttamente con i servizi dell'area di lavoro. Metodi di estensione sul `IWorkspace` sono disponibili per i servizi forniti da Visual Studio, ad esempio <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. L'estensione può offrire un servizio dell'area di lavoro per i componenti all'interno dell'estensione o per altre estensioni da utilizzare. I consumer utilizzino <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> o un metodo di estensione fornito dal `IWorkspace` tipo.

>[!WARNING]
> Non creare servizi che sono in conflitto con Visual Studio. Si possono verificare problemi imprevisti.

## <a name="disposal-on-workspace-closure"></a>Eliminazione nella chiusura dell'area di lavoro

In chiusura di un'area di lavoro, potrebbe essere necessario Extender dispose ma una chiamata asincrona codice. Il <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> interfaccia è disponibile per consentire di scrivere questo codice semplice.

## <a name="related-types"></a>Tipi correlati

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> è l'entità centrale per un'area di lavoro aperto, ad esempio una cartella aperta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> Crea un provider per ogni area di lavoro creata un'istanza.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> Crea un servizio per ogni area di lavoro creata un'istanza.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> devono essere implementati in provider e i servizi che devono eseguire codice asincrono durante l'eliminazione.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornisce metodi helper per l'accesso ai servizi noti o servizi arbitrari.

## <a name="workspace-settings"></a>Impostazioni dell'area di lavoro

Aree di lavoro includono un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servizio con un controllo semplice ma potente su un'area di lavoro. Per una panoramica di base delle impostazioni, vedere [personalizzare la compilazione e il debug di attività](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

Le impostazioni per la maggior parte `SettingsType` sono tipi _. JSON_ i file, ad esempio _vsworkspacesettings. JSON_ e _Tasks_.

La potenza di impostazioni dell'area di lavoro incentri "ambiti", che sono semplicemente i percorsi nell'area di lavoro. Quando un consumer chiama <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>, vengono aggregati tutti gli ambiti che includono il percorso richiesto e il tipo di impostazione. Priorità di aggregazione di ambito è il seguente:

1. "Impostazioni locali", che è in genere la radice area di lavoro `.vs` directory.
1. Il percorso richiesto stesso.
1. La directory padre del percorso di richiesta.
1. Directory fino a quella inclusa la radice dell'area di lavoro tutti ulteriormente padre.
1. "Impostazioni globali", ovvero in una directory dell'utente.

Il risultato è un'istanza di <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>. Questo oggetto contiene le impostazioni per un tipo particolare e possono eseguire query per l'impostazione di nomi delle chiavi archiviate come `string`. Il <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> metodi e <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> i metodi di estensione prevede che il chiamante deve conoscere il tipo del valore dell'impostazione richiesto. Poiché la maggior parte dei file di impostazioni vengono rese persistenti come _. JSON_ i file, molte chiamate userà `string`, `bool`, `int`e matrici di questi tipi. Sono supportati anche i tipi di oggetto. In questi casi, è possibile usare `IWorkspaceSettings` se stesso come argomento di tipo. Ad esempio:

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

Supponendo che queste impostazioni sono stati in cui un utente _vsworkspacesettings. JSON_, i dati sono accessibili come:

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
>Queste impostazioni API non sono correlate alle API disponibile nel `Microsoft.VisualStudio.Settings` dello spazio dei nomi. Le impostazioni dell'area di lavoro sono indipendente dell'host e usano file di impostazioni specifiche dell'area di lavoro o i provider di impostazioni dinamiche.

### <a name="providing-dynamic-settings"></a>Fornendo impostazioni dinamiche

Le estensioni possono fornire <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s. Questi provider in memoria consentono le estensioni per aggiungere le impostazioni o eseguire l'override di altri utenti.

Esportazione di un `IWorkspaceSettingsProvider` è diverso rispetto ad altri provider dell'area di lavoro. La factory non è `IWorkspaceProviderFactory` e nessun tipo di attributo speciali. Implementare invece <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> e usare `[Export(typeof(IWorkspaceSettingsProviderFactory))]`.

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
>Quando si implementa i metodi che restituiscono `IWorkspaceSettingsSource` (ad esempio `IWorkspaceSettingsProvider.GetSingleSettings`), restituire un'istanza di `IWorkspaceSettings` anziché `IWorkspaceSettingsSource`. `IWorkspaceSettings` vengono fornite ulteriori informazioni che possono essere utili durante alcune aggregazioni di impostazioni.

### <a name="settings-related-apis"></a>API correlate alle impostazioni

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> impostazioni di letture e le aggregazioni per area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> Ottiene il `IWorkspaceSettingsManager` per un'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> Ottiene le impostazioni per un determinato ambito aggregato per tutti gli ambiti sovrapposti.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene le impostazioni per un determinato ambito.

## <a name="workspace-suggested-practices"></a>Area di lavoro suggeriti procedure consigliate

- Restituire gli oggetti dal `IWorkspaceProviderFactory.CreateProvider` o le API simili che memorizzano le `Workspace` contesto quando creato. Le interfacce i provider vengono scritte aspetta che questo oggetto viene mantenuto durante la creazione.
- Salvare le impostazioni all'interno del percorso "Impostazioni locali" dell'area di lavoro o le cache specifiche dell'area di lavoro. Creare un percorso per il file utilizzando `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` in Visual Studio 2017 versione 15.6 o versione successiva. Nelle versioni precedenti alla versione 15.6, usare il frammento seguente:

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

## <a name="solution-events-and-package-auto-load"></a>Gli eventi della soluzione e auto-caricamento del pacchetto

I pacchetti caricati possono implementare `IVsSolutionEvents7` e richiamare `IVsSolution.AdviseSolutionEvents`. Include gli eventi su apertura e chiusura di una cartella in Visual Studio.

Un contesto dell'interfaccia utente utilizzabile per il caricamento automatico del pacchetto. Il valore è `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Il pacchetto SourceExplorerPackage non è stato caricato correttamente

Estendibilità dell'area di lavoro è principalmente basato su MEF e gli errori di composizione causerà il pacchetto di hosting di Apri cartella per il caricamento ha esito negativo. Ad esempio, se un'estensione consente di esportare un tipo con `ExportFileContextProviderAttribute`, ma il tipo implementa solo `IWorkspaceProviderFactory<IFileContextActionProvider>`, si verificherà un errore durante il tentativo di aprire una cartella in Visual Studio. I dettagli dell'errore sono reperibile nel _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_. Risolvere gli eventuali errori per i tipi implementati dall'estensione.

## <a name="next-steps"></a>Passaggi successivi

* [I contesti di file](workspace-file-contexts.md) -provider di contesto File bring intelligence codice per le aree di lavoro di Apri cartella.
* [L'indicizzazione](workspace-indexing.md) -area di lavoro di indicizzazione raccoglie e rende persistenti le informazioni sull'area di lavoro.
