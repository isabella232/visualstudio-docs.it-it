---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Professional 2019
titleSuffix: ''
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 12/03/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: a785f03f5588b951f9473ef6c4a88099c33d44f1
ms.sourcegitcommit: 3b48ce4649d38a7e3b095bd087739d6131e49d1b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76158833"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Editor principale di Visual Studio (incluso in Visual Studio Professional 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrizione:** shell di base di Visual Studio, che include un editor di codice con riconoscimento della sintassi, il controllo del codice sorgente e la gestione degli elementi di lavoro.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 16.1.28811.260 | Richiesto
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Pagina iniziale di Visual Studio per utenti di C++ | 16.0.28315.86 | Facoltativa

## <a name="azure-development"></a>Sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrizione:** Azure SDK, strumenti e progetti per lo sviluppo di app cloud e la creazione di risorse con .NET Core e .NET Framework. Include anche strumenti per inserimento l'applicazione, incluso il supporto per docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Richiesto
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Richiesto
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. DevelopmentTools | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft. NetCore. Component. Web | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Richiesto
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Richiesto
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prerequisiti per lo sviluppo per Azure | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Richiesto
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Richiesto
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommended (Consigliati)
Microsoft.Net.Core.Component.SDK.2.1 | Runtime di .NET Core 2,1 LTS | 16.4.29519.181 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools per Kubernetes | 16.0.28625.61 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. Azure. PowerShell | Azure PowerShell | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Strumenti di base di Azure Resource Manager | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Strumenti di Service Fabric | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Strumenti di Servizi cloud di Azure | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Strumenti di Azure Resource Manager | 16.0.28528.71 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 Targeting Pack | 16.4.29313.120 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativa
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | Strumenti di sviluppo .NET Framework 4,8 | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy di Archiviazione di Azure | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativa

## <a name="data-storage-and-processing"></a>Archiviazione ed elaborazione dei dati

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrizione:** consente di connettere, sviluppare e testare soluzioni dati con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Recommended (Consigliati)
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Recommended (Consigliati)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommended (Consigliati)
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativa

## <a name="data-science-and-analytical-applications"></a>Applicazioni analitiche e di analisi scientifica dei dati

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrizione:** Linguaggi e strumenti per la creazione di applicazioni data science, tra cui F#Python e.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Recommended (Consigliati)
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Recommended (Consigliati)
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.2.29020.229 | Facoltativa
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativa

## <a name="net-desktop-development"></a>Sviluppo per desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrizione:** Crea applicazioni WPF, Windows Forms e console usando C#, Visual Basic e F# con .NET Core e .NET Framework.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommended (Consigliati)
Microsoft.Net.Core.Component.SDK.2.1 | Runtime di .NET Core 2,1 LTS | 16.4.29519.181 | Recommended (Consigliati)
Microsoft. NetCore. Component. DevelopmentTools | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Recommended (Consigliati)
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Facoltativa
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativa
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativa
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 Targeting Pack | 16.4.29313.120 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativa
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | Strumenti di sviluppo .NET Framework 4,8 | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativa
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facoltativa
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativa
Microsoft. VisualStudio. ComponentGroup. MSIX. Packaging | Strumenti per la creazione di pacchetti MSIX | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Facoltativa

## <a name="game-development-with-unity"></a>Sviluppo di giochi con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrizione:** consente di creare giochi 2D e 3D con Unity, un potente ambiente di sviluppo multipiattaforma.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools per Unity | 16.0.28315.86 | Richiesto
Component.UnityEngine.x64 | Editor di Unity 2019,2 a 64 bit | 16.4.29429.68 | Recommended (Consigliati)
Component.UnityEngine.x86 | Editor di Unity 5.6 a 32 bit | 16.1.28811.260 | Recommended (Consigliati)

## <a name="linux-development-with-c"></a>Sviluppo di applicazioni Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrizione:** consente di creare ed eseguire il debug di applicazioni eseguite in un ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.MDD.Linux | C++ per lo sviluppo di applicazioni Linux | 16.4.29511.114 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Richiesto
Component.Linux.CMake | Strumenti CMake C++ per Linux | 16.2.29003.222 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Recommended (Consigliati)
Component.MDD.Linux.GCC.arm | Strumenti di sviluppo Embedded e IoT | 16.4.29429.68 | Facoltativa

## <a name="desktop-development-with-c"></a>Sviluppo di applicazioni desktop con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrizione:** Crea app C++ moderne per Windows usando gli strumenti che preferisci, tra cui MSVC, Clang, cmake o MSBuild.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.2.29012.281 | Richiesto
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. VC. ASAN | C++AddressSanitizer (sperimentale) | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.ATL | C++ATL per gli strumenti di compilazione V142 più recenti (x86 & x64) | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti CMake C++ per Windows | 16.3.29103.31 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adattatore di test per Boost.Test | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Recommended (Consigliati)
Microsoft. VisualStudio. ComponentGroup. WebToolsExtensions. CMake | Editor JSON | 16.3.29207.166 | Recommended (Consigliati)
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativa
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Facoltativa
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Facoltativa
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Facoltativa
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.ATLMFC | C++MFC per gli strumenti di compilazione V142 più recenti (x86 & x64) | 16.4.29313.120 | Facoltativa
Microsoft.VisualStudio.Component.VC.CLI.Support | C++Supporto di/CLI per gli strumenti di compilazione V142 (14,24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.VC.Llvm.Clang | C++Compilatore Clang per Windows (9.0.0) | 16.4.29511.114 | Facoltativa
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | Clang-cl C++ per Build Tools v142 (x64/x86) | 16.3.29207.166 | Facoltativa
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli C++ per Build Tools v142 (x64/x86 - sperimentale) | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | C++Strumenti Clang per Windows (9.0.0-x64/x86) | 16.4.29511.114 | Facoltativa

## <a name="game-development-with-c"></a>Sviluppo di giochi con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrizione:** consente di sfruttare tutte le funzionalità di C++ per compilare giochi professionali basati su DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. VC. ASAN | C++AddressSanitizer (sperimentale) | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Recommended (Consigliati)
Component.Android.NDK.R16B | Android NDK (R16B) | 16.4.29519.181 | Facoltativa
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Facoltativa
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Facoltativa
Component.Cocos | Cocos | 16.0.28315.86 | Facoltativa
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativa
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Facoltativa
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Facoltativa
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Facoltativa
Component.Unreal | Programma di installazione di Unreal Engine | 16.1.28810.153 | Facoltativa
Component.Unreal.Android | Supporto IDE Android per Unreal Engine | 16.1.28810.153 | Facoltativa
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Facoltativa
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Facoltativa
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativa
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativa

## <a name="mobile-development-with-c"></a>Sviluppo di app per dispositivi mobili con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Richiesto
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Richiesto
Component.Android.NDK.R16B | Android NDK (R16B) | 16.4.29519.181 | Recommended (Consigliati)
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Recommended (Consigliati)
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Recommended (Consigliati)
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (a 32 bit) | 16.4.29519.181 | Facoltativa
Component.Google.Android.Emulator.API25.Private | Emulatore Google Android (livello API 25) (installazione locale) | 16.1.28810.153 | Facoltativa
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (installazione locale) | 16.0.28528.71 | Facoltativa
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.0.28528.71 | Facoltativa
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.10 | Facoltativa
Component.MDD.IOS | Strumenti di sviluppo per app iOS in C++ | 16.0.28517.75 | Facoltativa

## <a name="net-core-cross-platform-development"></a>Sviluppo multipiattaforma .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrizione:** consente di creare applicazioni multipiattaforma con .NET Core, ASP.NET Core, HTML/JavaScript e contenitori con il supporto di Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Richiesto
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. DevelopmentTools | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft. NetCore. Component. Web | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Richiesto
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Richiesto
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Recommended (Consigliati)
Microsoft.Net.Core.Component.SDK.2.1 | Runtime di .NET Core 2,1 LTS | 16.4.29519.181 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.2.29003.222 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativa
Microsoft. VisualStudio. ComponentGroup. MSIX. Packaging | Strumenti per la creazione di pacchetti MSIX | 16.4.29409.204 | Facoltativa

## <a name="mobile-development-with-net"></a>Sviluppo di applicazioni per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Richiesto
Component.Xamarin | Xamarin | 16.4.29409.204 | Richiesto
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. DevelopmentTools | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.Merq | Strumenti interni comuni Xamarin | 16.2.29012.281 | Richiesto
Microsoft.VisualStudio.Component.MonoDebugger | Debugger di Mono | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motore di creazione modello ASP.NET | 16.0.28315.86 | Richiesto
Component.Android.SDK28 | Programma di installazione di Android SDK (livello API 28) | 16.2.29003.222 | Recommended (Consigliati)

## <a name="aspnet-and-web-development"></a>Sviluppo ASP.NET e Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrizione:** Crea applicazioni Web con ASP.NET Core, ASP.NET, HTML/JavaScript e contenitori, incluso il supporto per docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Richiesto
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. DevelopmentTools | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft. NetCore. Component. Web | Strumenti di sviluppo per .NET Core | 16.4.29511.114 | Richiesto
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Richiesto
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Recommended (Consigliati)
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Recommended (Consigliati)
Microsoft.Net.Core.Component.SDK.2.1 | Runtime di .NET Core 2,1 LTS | 16.4.29519.181 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.2.29003.222 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 Targeting Pack | 16.4.29313.120 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativa
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | Strumenti di sviluppo .NET Framework 4,8 | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Modelli di progetto aggiuntivi (versioni precedenti) | 16.0.28621.142 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativa

## <a name="nodejs-development"></a>Sviluppo Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni. 

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.Node.Tools | Strumenti di sviluppo Node.js | 16.4.29429.68 | Richiesto
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Richiesto
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa

## <a name="officesharepoint-development"></a>Sviluppo per Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrizione:** consente di creare componenti aggiuntivi per Office e SharePoint, soluzioni SharePoint e componenti aggiuntivi VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Richiesto
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools per Visual Studio | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Richiesto
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Richiesto
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Richiesto
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools per Office (VSTO) | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net. Component. 4.8. TargetingPack | .NET Framework 4,8 Targeting Pack | 16.4.29313.120 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativa
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativa
Microsoft.Net. ComponentGroup. 4.8. DeveloperTools | Strumenti di sviluppo .NET Framework 4,8 | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Facoltativa

## <a name="python-development"></a>Sviluppo Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrizione:** modifica, debug, sviluppo interattivo e controllo del codice per Python.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.4.29429.68 | Richiesto
Component.CPython3.x64 | Python 3 64 bit (3.7.5) | 3.7.5 | Recommended (Consigliati)
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1076 | Recommended (Consigliati)
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Recommended (Consigliati)
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.4.29409.204 | Recommended (Consigliati)
Microsoft. VisualStudio. Component. TypeScript. 3.7 | SDK di TypeScript 3,7 | 16.0.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Recommended (Consigliati)
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo ASP.NET e Web | 16.0.28621.142 | Recommended (Consigliati)
Component.CPython2.x64 | Python 2 a 64 bit (2.7.16) | 2.7.16 | Facoltativa
Component.CPython2.x86 | Python 2 a 32 bit (2.7.16) | 2.7.16 | Facoltativa
Component.CPython3.x86 | Python 3 32 bit (3.7.5) | 3.7.5 | Facoltativa
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativa
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativa
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Facoltativa
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.2.29020.229 | Facoltativa
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativa
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Facoltativa
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Facoltativa
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Facoltativa
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Facoltativa
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Facoltativa
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Facoltativa
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Facoltativa
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativa
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativa
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativa
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facoltativa
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Facoltativa

## <a name="universal-windows-platform-development"></a>Sviluppo della piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrizione:** Creare applicazioni per la piattaforma UWP (Universal Windows Platform) con C#, VB o facoltativamente C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.4.29429.68 | Richiesto
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Richiesto
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NetCore. Component. SDK | SDK di .NET Core 3,1 | 16.4.29519.181 | Richiesto
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 16.0.28517.75 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Richiesto
Microsoft. VisualStudio. ComponentGroup. MSIX. Packaging | Strumenti per la creazione di pacchetti MSIX | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native e .NET Standard | 16.3.29102.218 | Richiesto
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Strumenti della piattaforma UWP (Universal Windows Platform) | 16.4.29409.204 | Richiesto
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin | 16.4.29511.114 | Richiesto
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Facoltativa
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Facoltativa
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Supporto della piattaforma UWP (Universal Windows Platform) C++ per Build Tools v142 (ARM64) | 16.3.29207.166 | Facoltativa
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativa
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC V142-VS 2019 C++ arm64 Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.24) | 16.4.29409.204 | Facoltativa
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ Build Tools ARM (v14.16) | 16.2.29003.222 | Facoltativa
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ Build Tools ARM64 (v14.16) | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativa
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Connettività dispositivi USB | 16.4.29511.114 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.2.29012.281 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v142) | 16.3.29207.166 | Facoltativa
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v141) | 16.1.28810.153 | Facoltativa

## <a name="visual-studio-extension-development"></a>Sviluppo di estensioni di Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrizione:** consente di creare componenti aggiuntivi ed estensioni per Visual Studio, inclusi nuovi comandi, analizzatori del codice e finestre degli strumenti.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Name | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.4.29429.68 | Richiesto
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Richiesto
Microsoft. NET. Component. 4.8. SDK | SDK .NET Framework 4,8 | 16.4.29313.120 | Richiesto
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Richiesto
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0.1 | Richiesto
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Richiesto
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.4.29429.68 | Richiesto
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Richiesto
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prerequisiti per lo sviluppo di estensioni di Visual Studio | 16.4.29318.151 | Richiesto
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.4.29429.68 | Recommended (Consigliati)
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Recommended (Consigliati)
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.2.29003.222 | Facoltativa
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.4.29429.68 | Facoltativa
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | Facoltativa

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | Name | Versione
--- | --- | ---
Component.GitHub.VisualStudio | Estensione GitHub per Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Help Viewer | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | Runtime di .NET Core 2,2 | 16.4.29519.181
Microsoft. NET. Core. Component. SDK. 3.0 | Runtime di .NET Core 3,0 | 16.4.29519.181
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo e .NET Core 2,1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Strumenti di sviluppo Web più .NET Core 2,1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integrazione di Office con Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Convalida delle dipendenze | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | Git per Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Strumenti di LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ATL | ATL C++ v14.20 per Build Tools v142 (x86 e x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | ATL C++ v14.20 per Build Tools v142 (ARM) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | ATL C++ v14.20 per Build Tools v142 (ARM64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | MFC C++ v14.20 per Build Tools v142 (x86 e x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | MFC C++ v14.20 per Build Tools v142 (ARM) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | MFC C++ v14.20 per Build Tools v142 (ARM64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.20) | 16.4.29511.114
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.21) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.21) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.ATL | ATL C++ v14.21 per Build Tools v142 (x86 e x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | ATL C++ v14.21 per Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | ATL C++ v14.21 per Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | MFC C++ v14.21 per Build Tools v142 (x86 e x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | MFC C++ v14.21 per Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | MFC C++ v14.21 per Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.21) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.22) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ARM. Spectre | Librerie con mitigazione Spectre ARM MSVC v142 - VS 2019 C++ (v14.22) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.22) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ARM64. Spectre | Librerie con mitigazione Spectre ARM64 MSVC v142 - VS 2019 C++ (v14.22) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. ATL | C++v 14.22 ATL per gli strumenti di compilazione V142 (x86 & x64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM | C++v 14.22 ATL per V142 Build Tools (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM. Spectre | C++v 14.22 ATL per V142 strumenti di compilazione con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64 | C++v 14.22 ATL per V142 Build Tools (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. ATL. ARM64. Spectre | C++v 14.22 ATL per V142 strumenti di compilazione con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. ATL. Spectre | C++v 14.22 ATL per V142 strumenti di compilazione con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. CLI. support | Supporto C++/CLI per Build Tools v142 (14.22) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC | C++v 14.22 MFC per V142 Build Tools (x86 & x64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM | C++v 14.22 MFC per V142 Build Tools (ARM) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM. Spectre | C++v 14.22 MFC per V142 Build Tools con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64 | C++v 14.22 MFC per V142 Build Tools (ARM64) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. MFC. ARM64. Spectre | C++v 14.22 MFC per V142 Build Tools con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. MFC. Spectre | C++v 14.22 MFC per V142 Build Tools con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.22) | 16.4.29313.120
Microsoft. VisualStudio. Component. VC. 14.22. x86. x64. Spectre | Librerie con mitigazione Spectre x64/x86 MSVC v142 - VS 2019 C++ (v14.22) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ARM | MSVC V142-VS 2019 C++ ARM Build Tools (v 14.23) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ARM. Spectre | MSVC V142-VS 2019 C++ ARM Spectre-mitigated libs (v 14.23) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ARM64 | MSVC V142-VS 2019 C++ arm64 Build Tools (v 14.23) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ARM64. Spectre | MSVC V142-VS 2019 C++ arm64 Spectre-mitigated libs (v 14.23) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL | C++v 14.23 ATL per gli strumenti di compilazione V142 (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM | C++v 14.23 ATL per V142 Build Tools (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM. Spectre | C++v 14.23 ATL per V142 strumenti di compilazione con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64 | C++v 14.23 ATL per V142 Build Tools (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL. ARM64. Spectre | C++v 14.23 ATL per V142 strumenti di compilazione con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. ATL. Spectre | C++v 14.23 ATL per V142 strumenti di compilazione con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. CLI. support | C++Supporto di/CLI per gli strumenti di compilazione V142 (14,23) | 16.4.29409.204
Microsoft. VisualStudio. Component. VC. 14.23. MFC | C++v 14.23 MFC per V142 Build Tools (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. MFC. ARM | C++v 14.23 MFC per V142 Build Tools (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. MFC. ARM. Spectre | C++v 14.23 MFC per V142 Build Tools con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. MFC. ARM64 | C++v 14.23 MFC per V142 Build Tools (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. MFC. ARM64. Spectre | C++v 14.23 MFC per V142 Build Tools con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. MFC. Spectre | C++v 14.23 MFC per V142 Build Tools con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64 | MSVC V142-VS 2019 C++ x64/x86 Build Tools (v 14.23) | 16.4.29429.68
Microsoft. VisualStudio. Component. VC. 14.23. x86. x64. Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-mitigated libs (v 14.23) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.ATL.ARM | C++ATL per gli strumenti di compilazione V142 più recenti (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | C++ATL per gli ultimi strumenti di compilazione V142 con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | C++ATL per gli strumenti di compilazione V142 più recenti (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | C++ATL per gli strumenti di compilazione V142 più recenti con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.ATL.Spectre | C++ATL per gli strumenti di compilazione V142 più recenti con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | C++MFC per gli strumenti di compilazione V142 più recenti con mitigazioni Spectre (x86 & x64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.MFC.ARM | C++MFC per gli strumenti di compilazione V142 più recenti (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | C++MFC per gli strumenti di compilazione V142 più recenti con mitigazioni Spectre (ARM) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | C++MFC per gli strumenti di compilazione V142 più recenti (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | C++MFC per gli strumenti di compilazione V142 più recenti con mitigazioni Spectre (ARM64) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSM di C++ 2019 Redistributable | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC V142-VS 2019 C++ ARM Spectre-mitigated libs (v 14.24) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC V142-VS 2019 C++ arm64 Spectre-mitigated libs (v 14.24) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC V142-VS 2019 C++ x64/x86 Spectre-mitigated libs (v 14.24)  | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM VS 2017 C++ (v14.16) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM64 VS 2017 C++ (v14.16) | 16.4.29429.68
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL C++ per Build Tools v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL C++ per Build Tools v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | ATL C++ per Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | Supporto C++/CLI per Build Tools v141 (14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | MFC C++ per Build Tools v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | MFC C++ per Build Tools v141 (ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | MFC C++ per Build Tools v141 (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | MFC C++ per Build Tools v141 con mitigazioni Spectre (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - Librerie con mitigazione Spectre x64/x86 VS 2017 C++ (v14.16) | 16.4.29429.68
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Supporto di Windows XP C++ per strumenti VS 2017 (v141) [deprecato] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
