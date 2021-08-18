---
title: Aree di lavoro in Visual Studio | Microsoft Docs
description: Informazioni su Visual Studio un'area di lavoro per rappresentare una raccolta di file in Apri cartella, inclusi i provider e i servizi dell'area di lavoro.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 95b2df98d3a06e4a2e2b667b8158c310a07d2c27dfe3bf33c9869ec5b138f45f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447597"
---
# <a name="workspaces"></a>Aree di lavoro

Un'area di Visual Studio rappresenta qualsiasi raccolta di file in [Open Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)ed è rappresentata dal <xref:Microsoft.VisualStudio.Workspace.IWorkspace> tipo . Di per sé, l'area di lavoro non comprende il contenuto o le funzionalità correlate ai file all'interno della cartella. Fornisce invece un set generale di API per le funzionalità e le estensioni per produrre e utilizzare dati su cui altri utenti possono agire. I produttori sono composti tramite il [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) usando vari attributi di esportazione.

## <a name="workspace-providers-and-services"></a>Provider e servizi dell'area di lavoro

I provider e i servizi dell'area di lavoro forniscono i dati e le funzionalità per reagire al contenuto di un'area di lavoro. Possono fornire informazioni contestuali sui file, simboli nei file di origine o funzionalità di compilazione.

Entrambi i concetti usano un [modello factory](https://en.wikipedia.org/wiki/Factory_method_pattern) e vengono importati tramite MEF dall'area di lavoro. Tutti gli attributi di `IProviderMetadataBase` esportazione implementano o , ma esistono tipi concreti che le estensioni devono usare per i tipi `IWorkspaceServiceFactoryMetadata` esportati.

Una differenza tra provider e servizi è la loro relazione con l'area di lavoro. Un'area di lavoro può avere molti provider di un determinato tipo, ma viene creato un solo servizio di un tipo specifico per ogni area di lavoro. Ad esempio, un'area di lavoro ha molti provider di utilità di analisi file, ma l'area di lavoro include un solo servizio di indicizzazione per ogni area di lavoro.

Un'altra differenza chiave è l'utilizzo di dati da provider e servizi. L'area di lavoro è il punto di ingresso per ottenere dati dai provider per due motivi. In primo luogo, i provider hanno in genere un set ristretto di dati creati. I dati possono essere simboli per un file di origine C# o contesti di file di compilazione per _un_ CMakeLists.txtfile. L'area di lavoro corrisponderà alla richiesta di un consumer ai provider i cui metadati sono allineati alla richiesta. In secondo piano, alcuni scenari consentono a molti provider di contribuire a una richiesta, mentre altri scenari usano il provider con la priorità più alta.

Al contrario, le estensioni possono ottenere istanze di e interagire direttamente con i servizi dell'area di lavoro. I metodi di `IWorkspace` estensione in sono disponibili per i servizi forniti da Visual Studio, ad esempio <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . L'estensione può offrire un servizio dell'area di lavoro per i componenti all'interno dell'estensione o per l'utilizzo di altre estensioni. I consumer devono <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> usare o un metodo di estensione specificato nel `IWorkspace` tipo.

>[!WARNING]
> Non creare servizi in conflitto con Visual Studio. Può causare problemi imprevisti.

## <a name="disposal-on-workspace-closure"></a>Eliminazione alla chiusura dell'area di lavoro

Alla chiusura di un'area di lavoro, gli extender potrebbero dover eliminare ma chiamare codice asincrono. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>L'interfaccia è disponibile per semplificare la scrittura di questo codice.

## <a name="related-types"></a>Tipi correlati

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> è l'entità centrale per un'area di lavoro aperta come una cartella aperta.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> crea un provider per ogni area di lavoro di cui è stata creata un'istanza.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> crea un servizio per ogni area di lavoro di cui è stata creata un'istanza.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> deve essere implementato nei provider e nei servizi che devono eseguire codice asincrono durante l'eliminazione.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> fornisce metodi helper per l'accesso a servizi noti o servizi arbitrari.

## <a name="workspace-settings"></a>Impostazioni dell'area di lavoro

Le aree di lavoro hanno un <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> servizio con controllo semplice ma potente su un'area di lavoro. Per una panoramica di base delle impostazioni, vedere [Personalizzare le attività di compilazione e debug.](../ide/customize-build-and-debug-tasks-in-visual-studio.md)

Impostazioni per la maggior parte dei tipi sono file JSON, ad esempioVSWorkspaceSettings.js`SettingsType` _su_ e _tasks.vs.jsin_. 

La potenza delle impostazioni dell'area di lavoro è centrata su "ambiti", che sono semplicemente percorsi all'interno dell'area di lavoro. Quando un consumer chiama , vengono aggregati tutti gli ambiti che includono il percorso richiesto e il <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> tipo di impostazione. La priorità di aggregazione dell'ambito è la seguente:

1. "Impostazioni locali", che in genere è la directory della radice dell'area di `.vs` lavoro.
1. Percorso richiesto.
1. Directory padre del percorso richiesto.
1. Tutte le altre directory padre fino alla radice dell'area di lavoro inclusa.
1. "Impostazioni globali", che si trova in una directory utente.

Il risultato è un'istanza di <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . Questo oggetto contiene le impostazioni per un particolare tipo e può essere sottoposto a query per l'impostazione dei nomi di chiave archiviati come `string` . I <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A> metodi e i metodi di estensione prevedono che il <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> chiamante sappia il tipo del valore di impostazione richiesto. Poiché la maggior parte dei file di impostazioni viene mantenuta come file _JSON,_ molte chiamate useranno `string` matrici `bool` , , e di `int` questi tipi. Sono supportati anche i tipi di oggetto. In questi casi, è possibile usare `IWorkspaceSettings` se stesso come argomento di tipo. Esempio:

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

Supponendo che queste impostazioni si trovavano nelVSWorkspaceSettings.jsdi un utente _in_, è possibile accedere ai dati come:

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
>Queste API delle impostazioni non sono correlate alle API disponibili nello spazio dei `Microsoft.VisualStudio.Settings` nomi . Le impostazioni dell'area di lavoro sono indipendenti dall'host e usano file di impostazioni specifici dell'area di lavoro o provider di impostazioni dinamiche.

### <a name="providing-dynamic-settings"></a>Fornire impostazioni dinamiche

Le estensioni possono fornire <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> s. Questi provider in memoria consentono alle estensioni di aggiungere impostazioni o eseguire l'override di altri.

L'esportazione di un `IWorkspaceSettingsProvider` oggetto è diversa da altri provider dell'area di lavoro. La factory non è `IWorkspaceProviderFactory` e non esiste alcun tipo di attributo speciale. Implementare e <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> usare `[Export(typeof(IWorkspaceSettingsProviderFactory))]` invece .

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
>Quando si implementano metodi che `IWorkspaceSettingsSource` restituiscono (ad esempio `IWorkspaceSettingsProvider.GetSingleSettings` ), restituiscono un'istanza di `IWorkspaceSettings` anziché `IWorkspaceSettingsSource` . `IWorkspaceSettings` fornisce altre informazioni che possono essere utili durante alcune aggregazioni di impostazioni.

### <a name="settings-related-apis"></a>Impostazioni API correlate

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> legge e aggrega le impostazioni per l'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> ottiene l'oggetto `IWorkspaceSettingsManager` per un'area di lavoro.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> ottiene le impostazioni per un determinato ambito aggregato in tutti gli ambiti sovrapposti.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> contiene le impostazioni per un ambito specifico.

## <a name="workspace-suggested-practices"></a>Procedure consigliate per l'area di lavoro

- Restituisce oggetti da `IWorkspaceProviderFactory.CreateProvider` o API simili che ricordano il contesto al momento della `Workspace` creazione. Le interfacce dei provider vengono scritte prevedendo che questo oggetto sia mantenuto al momento della creazione.
- Salvare le impostazioni o le cache specifiche dell'area di lavoro nel percorso "Impostazioni locali" dell'area di lavoro. Creare un percorso per il file `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` usando in Visual Studio 2017 versione 15.6 o successiva. Per le versioni precedenti alla versione 15.6, usare il frammento di codice seguente:

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

## <a name="solution-events-and-package-auto-load"></a>Eventi della soluzione e caricamento automatico dei pacchetti

I pacchetti caricati possono implementare `IVsSolutionEvents7` e richiamare `IVsSolution.AdviseSolutionEvents` . Include l'evento all'apertura e alla chiusura di una cartella in Visual Studio.

Un contesto dell'interfaccia utente può essere usato per caricare automaticamente il pacchetto. Il valore è `4646B819-1AE0-4E79-97F4-8A8176FDD664`.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>Il pacchetto SourceExplorerPackage non è stato caricato correttamente

L'estendibilità dell'area di lavoro è fortemente basata su MEF e gli errori di composizione causeranno il caricamento del pacchetto che ospita Open Folder. Ad esempio, se un'estensione esporta un tipo con , ma il tipo implementa solo , si verificherà un errore quando si tenta di aprire una cartella `ExportFileContextProviderAttribute` `IWorkspaceProviderFactory<IFileContextActionProvider>` in Visual Studio.

::: moniker range="vs-2017"

I dettagli dell'errore sono disponibili in _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err._ Risolvere eventuali errori per i tipi implementati dall'estensione.

::: moniker-end

::: moniker range=">=vs-2019"

I dettagli dell'errore sono disponibili in _%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err._ Risolvere eventuali errori per i tipi implementati dall'estensione.

::: moniker-end

## <a name="next-steps"></a>Passaggi successivi

* [Contesti di file:](workspace-file-contexts.md) i provider di contesti di file generano funzionalità di code intelligence per le aree di lavoro Apri cartella.
* [Indicizzazione: l'indicizzazione](workspace-indexing.md) dell'area di lavoro raccoglie e rende persistenti le informazioni sull'area di lavoro.
