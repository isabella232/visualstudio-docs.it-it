---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Professional 2019
titleSuffix: ''
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 03/16/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: e4d837a98b0c4e68699bf11e4c7c12381c0068ac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79437596"
---
## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2019"></a>Editor principale di Visual Studio (incluso in Visual Studio Professional 2019)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrizione:** shell di base di Visual Studio, che include un editor di codice con riconoscimento della sintassi, il controllo del codice sorgente e la gestione degli elementi di lavoro.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 16.1.28811.260 | Obbligatoria
Microsoft.VisualStudio.Component.StartPageExperiment.Cpp | Pagina iniziale di Visual Studio per utenti di C++ | 16.0.28315.86 | Facoltativo

## <a name="azure-development"></a>Sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrizione:** SDK, strumenti e progetti di Azure per lo sviluppo di app cloud e la creazione di risorse con .NET Core e .NET Framework. Include anche strumenti per il contenitore dell'applicazione, incluso il supporto Docker.Also includes tools for containerizing your application, including Docker support.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatoria
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Obbligatoria
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.DevelopmentTools | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.Web | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Obbligatoria
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Obbligatoria
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obbligatoria
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prerequisiti per lo sviluppo per Azure | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Obbligatoria
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.5.29721.120 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.Net.Core.Component.SDK.2.1 | Runtime LTS .NET Core 2.1 | 16.5.29905.7 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Kubernetes.Tools | Visual Studio Tools per Kubernetes | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.Powershell | Azure Powershell | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Strumenti di base di Azure Resource Manager | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Strumenti di Service Fabric | 16.4.29313.120 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Strumenti di Servizi cloud di Azure | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Strumenti di Azure Resource Manager | 16.0.28528.71 | Consigliato
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.TargetingPack | Pacchetto di destinazione di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Strumenti di sviluppo di .NET Framework 4.8 | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy di Archiviazione di Azure | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo

## <a name="data-storage-and-processing"></a>Archiviazione ed elaborazione dei dati

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrizione:** consente di connettere, sviluppare e testare soluzioni dati con SQL Server, Azure Data Lake o Hadoop.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Consigliato
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Consigliato
Microsoft.Component.Azure.DataLake.Tools | Strumenti per Azure Data Lake e analisi di flusso | 16.5.29721.120 | Consigliato
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Consigliato
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Consigliato
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativo

## <a name="data-science-and-analytical-applications"></a>Applicazioni analitiche e di analisi scientifica dei dati

**ID:** Microsoft.VisualStudio.Workload.DataScience

**Descrizione:** Linguaggi e strumenti per la creazione di applicazioni di data science, tra cui Python e F.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.5.29515.121 | Consigliato
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Consigliato
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.2.29020.229 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativo

## <a name="net-desktop-development"></a>Sviluppo per desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrizione:** Compilare WPF, Windows Form e applicazioni console utilizzando C , Visual Basic e F , con .NET Core e .NET Framework.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.5.29514.35 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.Net.Core.Component.SDK.2.1 | Runtime LTS .NET Core 2.1 | 16.5.29905.7 | Consigliato
Microsoft.NetCore.Component.DevelopmentTools | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Consigliato
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | Facoltativo
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativo
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.TargetingPack | Pacchetto di destinazione di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Strumenti di sviluppo di .NET Framework 4.8 | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.Desktop | Supporto per il linguaggio F# desktop | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativo
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Strumenti di creazione di pacchetti MSIX | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Facoltativo

## <a name="game-development-with-unity"></a>Sviluppo di giochi con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrizione:** consente di creare giochi 2D e 3D con Unity, un potente ambiente di sviluppo multipiattaforma.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools per Unity | 16.0.28315.86 | Obbligatoria
Component.UnityEngine.x64 | Unity 2019.2 Editor a 64 bit | 16.5.29515.121 | Consigliato
Component.UnityEngine.x86 | Editor di Unity 5.6 a 32 bit | 16.1.28811.260 | Consigliato

## <a name="linux-development-with-c"></a>Sviluppo di applicazioni Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrizione:** consente di creare ed eseguire il debug di applicazioni eseguite in un ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.MDD.Linux | C++ per lo sviluppo di applicazioni Linux | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatoria
Component.Linux.CMake | Strumenti CMake C++ per Linux | 16.2.29003.222 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Consigliato
Component.MDD.Linux.GCC.arm | Strumenti di sviluppo Embedded e IoT | 16.5.29515.121 | Facoltativo

## <a name="desktop-development-with-c"></a>Sviluppo per desktop con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrizione:** Crea le moderne app di C, in Windows, usando strumenti di tua scelta, tra cui MSVC, Clang, CMake o MSBuild.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.2.29012.281 | Obbligatoria
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.Component.VC.ASAN | C'è AddressSanitizer (Sperimentale) | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.VC.ATL | ATL di C' per gli ultimi strumenti di compilazione v142 (x86 & x64) | 16.4.29313.120 | Consigliato
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti CMake C++ per Windows | 16.3.29103.31 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForBoostTest | Adattatore di test per Boost.Test | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.VC.TestAdapterForGoogleTest | Test Adapter for Google Test | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.CMake | Editor JSON | 16.3.29207.166 | Consigliato
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.5.29721.120 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 16.0.28625.61 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ Build Tools (v14.00) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC di C'è per gli strumenti di compilazione v142 più recenti (x86 & x64) | 16.4.29313.120 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto per gli strumenti di compilazione v142 (14,25) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Compilatore Clang di C.C. per Windows (9.0.0) | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | Clang-cl C++ per Build Tools v142 (x64/x86) | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli C++ per Build Tools v142 (x64/x86 - sperimentale) | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Strumenti Clang di C'è per Windows (9.0.0 - x64/x86) | 16.5.29514.35 | Facoltativo

## <a name="game-development-with-c"></a>Sviluppo di giochi con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrizione:** consente di sfruttare tutte le funzionalità di C++ per compilare giochi professionali basati su DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.VC.ASAN | C'è AddressSanitizer (Sperimentale) | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Consigliato
Component.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Facoltativo
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Facoltativo
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Facoltativo
Component.Cocos | Cocos | 16.0.28315.86 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.5.29721.120 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facoltativo
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Facoltativo
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Facoltativo
Component.Unreal | Programma di installazione di Unreal Engine | 16.1.28810.153 | Facoltativo
Component.Unreal.Android | Supporto IDE Android per Unreal Engine | 16.1.28810.153 | Facoltativo
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Facoltativo
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativo

## <a name="mobile-development-with-c"></a>Sviluppo di app per dispositivi mobili con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Android.SDK25.Private | Programma di installazione di Android SDK (livello API 25) (installazione locale per sviluppo di applicazioni per dispositivi mobili con C++) | 16.0.28625.61 | Obbligatoria
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Obbligatoria
Component.Android.NDK.R16B | Android NDK (R16B) | 16.5.29916.74 | Consigliato
Component.Ant | Apache Ant (1.9.3) | 1.9.3.8 | Consigliato
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | 16.0.28517.75 | Consigliato
Component.Android.NDK.R16B_3264 | Android NDK (R16B) (a 32 bit) | 16.5.29916.74 | Facoltativo
Component.Google.Android.Emulator.API25.Private | Emulatore Google Android (livello API 25) (installazione locale) | 16.1.28810.153 | Facoltativo
Component.HAXM.Private | Intel Hardware Accelerated Execution Manager (HAXM) (installazione locale) | 16.0.28528.71 | Facoltativo
Component.Incredibuild | IncrediBuild - Accelerazione della compilazione | 16.5.29721.120 | Facoltativo
Component.IncredibuildMenu | IncrediBuildMenu | 1.5.0.13 | Facoltativo
Component.MDD.IOS | Strumenti di sviluppo per app iOS in C++ | 16.0.28517.75 | Facoltativo

## <a name="net-core-cross-platform-development"></a>Sviluppo multipiattaforma .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrizione:** consente di creare applicazioni multipiattaforma con .NET Core, ASP.NET Core, HTML/JavaScript e contenitori con il supporto di Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatoria
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.DevelopmentTools | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.Web | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Obbligatoria
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Consigliato
Microsoft.Net.Core.Component.SDK.2.1 | Runtime LTS .NET Core 2.1 | 16.5.29905.7 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.2.29003.222 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Strumenti di creazione di pacchetti MSIX | 16.4.29409.204 | Facoltativo

## <a name="mobile-development-with-net"></a>Sviluppo di applicazioni per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.OpenJDK | OpenJDK (distribuzione Microsoft) | 16.1.28811.260 | Obbligatoria
Component.Xamarin | Xamarin | 16.5.29721.120 | Obbligatoria
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 16.0.28315.86 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.DevelopmentTools | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.Merq | Strumenti interni comuni Xamarin | 16.2.29012.281 | Obbligatoria
Microsoft.VisualStudio.Component.MonoDebugger | Debugger di Mono | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions.TemplateEngine | Motore di creazione modello ASP.NET | 16.0.28315.86 | Obbligatoria
Component.Android.SDK28 | Programma di installazione di Android SDK (livello API 28) | 16.2.29003.222 | Consigliato

## <a name="aspnet-and-web-development"></a>Sviluppo Web e ASP.NET

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrizione:** Crea applicazioni web utilizzando ASP.NET Core, ASP.NET, HTML/JavaScript e Contenitori, incluso il supporto Docker.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatoria
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.DevelopmentTools | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.Web | Strumenti di sviluppo .NET Core | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.FSharp.WebTemplates | Supporto del linguaggio F# per progetti Web | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obbligatoria
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Obbligatoria
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Component.Microsoft.VisualStudio.Web.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28714.129 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 16.0.28516.191 | Consigliato
Microsoft.Net.Core.Component.SDK.2.1 | Runtime LTS .NET Core 2.1 | 16.5.29905.7 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 16.0.28625.61 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 16.0.28315.86 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.AzureFunctions | Strumenti per Processi Web di Azure | 16.0.28621.142 | Consigliato
Microsoft.VisualStudio.ComponentGroup.Web.CloudTools | Strumenti cloud per lo sviluppo Web | 16.2.29003.222 | Consigliato
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.TargetingPack | Pacchetto di destinazione di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Strumenti di sviluppo di .NET Framework 4.8 | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.AdditionalWebProjectTemplates | Modelli di progetto aggiuntivi (versioni precedenti) | 16.0.28621.142 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.IISDevelopment | Supporto IIS in fase di sviluppo | 16.0.28315.86 | Facoltativo

## <a name="nodejs-development"></a>Sviluppo Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni. 

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.Node.Tools | Strumenti di sviluppo Node.js | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Obbligatoria
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Facoltativo

## <a name="officesharepoint-development"></a>Sviluppo per Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrizione:** consente di creare componenti aggiuntivi per Office e SharePoint, soluzioni SharePoint e componenti aggiuntivi VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Obbligatoria
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | 16.5.29514.35 | Obbligatoria
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools per Visual Studio | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Obbligatoria
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 16.0.28625.61 | Obbligatoria
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Obbligatoria
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools per Office (VSTO) | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.TargetingPack | Pacchetto di destinazione di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 16.3.29207.166 | Facoltativo
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | Strumenti di sviluppo di .NET Framework 4.8 | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Sharepoint.WIF | Windows Identity Foundation 3.5 | 16.0.28621.142 | Facoltativo

## <a name="python-development"></a>Sviluppo Python

**ID:** Microsoft.VisualStudio.Workload.Python

**Descrizione:** modifica, debug, sviluppo interattivo e controllo del codice per Python.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.PythonTools | Supporto linguaggio Python | 16.5.29515.121 | Obbligatoria
Component.CPython3.x64 | Python 3 a 64 bit (3.7.5) | 3.7.5 | Consigliato
Component.Microsoft.VisualStudio.LiveShare | Live Share | 1.0.1561 | Consigliato
Microsoft.Component.PythonTools.Minicondax64 | Miniconda Python | 16.2.29003.222 | Consigliato
Microsoft.Component.PythonTools.Web | Supporto Web Python | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 16.4.29409.204 | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | 16.5.29721.120 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.3.8 | TypeScript 3.8 SDK | 16.0.29813.82 | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | 16.0.28517.75 | Consigliato
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | Sviluppo Web e ASP.NET | 16.0.28621.142 | Consigliato
Component.CPython2.x64 | Python 2 a 64 bit (2.7.16) | 2.7.16 | Facoltativo
Component.CPython2.x86 | Python 2 a 32 bit (2.7.16) | 2.7.16 | Facoltativo
Component.CPython3.x86 | Python 3 a 32 bit (3.7.5) | 3.7.5 | Facoltativo
Component.Microsoft.VisualStudio.RazorExtension | Servizi di linguaggio Razor | 16.0.28714.129 | Facoltativo
Component.Microsoft.Web.LibraryManager | Gestione librerie | 16.0.28315.86 | Facoltativo
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Facoltativo
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Strumenti di sviluppo nativo Python | 16.2.29020.229 | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Facoltativo
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Facoltativo
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Facoltativo
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Facoltativo
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | 16.1.28810.153 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | 16.4.29313.120 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | 16.4.29318.151 | Facoltativo
Microsoft.VisualStudio.Component.MSODBC.SQL | Driver ODBC di SQL Server | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.MSSQL.CMDLnUtils | SQL Server Command Line Utilities | 16.0.28707.177 | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 16.0.28315.86 | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 16.4.29409.204 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.Web | Prerequisiti per gli strumenti di sviluppo ASP.NET e Web | 16.4.29318.151 | Facoltativo

## <a name="universal-windows-platform-development"></a>Sviluppo della piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrizione:** Creare applicazioni per la piattaforma Windows universale con C , VB o, facoltativamente, in C.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.NetFX.Native | .NET Native | 16.5.29515.121 | Obbligatoria
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | 16.0.28315.86 | Obbligatoria
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.NetCore.Component.Runtime.3.1 | Runtime LTS .NET Core 3.1 | 16.5.29905.7 | Obbligatoria
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.5.29905.7 | Obbligatoria
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | 16.0.28517.75 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK (10.0.18362.0) | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.MSIX.Packaging | Strumenti di creazione di pacchetti MSIX | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.UWP.NetCoreAndStandard | .NET Native e .NET Standard | 16.3.29102.218 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.UWP.Support | Strumenti della piattaforma UWP (Universal Windows Platform) | 16.4.29409.204 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin | 16.5.29514.35 | Obbligatoria
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Facoltativo
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | Supporto della piattaforma UWP (Universal Windows Platform) C++ per Build Tools v142 (ARM64) | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base per C++ | 16.0.28625.61 | Facoltativo
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di C++ 2019 Redistributable | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - Strumenti di compilazione ARM di VS 2019 C | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - Strumenti di compilazione di VS 2019 C'ARM64 (v14.25) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.25) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 - VS 2017 C++ Build Tools ARM (v14.16) | 16.2.29003.222 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 - VS 2017 C++ Build Tools ARM64 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 - VS 2017 C++ Build Tools x64/x86 (v14.16) | 16.1.28829.92 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK (10.0.16299.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK (10.0.17763.0) | 16.0.28517.75 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.19041 | Windows 10 Preview SDK (10.0.19041.0) | 16.5.29721.120 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.IpOverUsb | Connettività dispositivi USB | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di C++ | 16.2.29012.281 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v142) | 16.3.29207.166 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141 | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ (v141) | 16.1.28810.153 | Facoltativo

## <a name="visual-studio-extension-development"></a>Sviluppo di estensioni di Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrizione:** consente di creare componenti aggiuntivi ed estensioni per Visual Studio, inclusi nuovi comandi, analizzatori del codice e finestre degli strumenti.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | Obbligatoria
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 Targeting Pack | 16.0.28517.75 | Obbligatoria
Microsoft.Net.Component.4.8.SDK | SDK di .NET Framework 4.8 | 16.4.29313.120 | Obbligatoria
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.7.2 | 16.3.29207.166 | Obbligatoria
Microsoft.VisualStudio.Component.IntelliCode | IntelliCode | 0,1 | Obbligatoria
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 16.1.28829.92 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 16.0.28714.129 | Obbligatoria
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 16.5.29515.121 | Obbligatoria
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 16.0.28315.86 | Obbligatoria
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prerequisiti per lo sviluppo di estensioni di Visual Studio | 16.4.29318.151 | Obbligatoria
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura .NET | 16.5.29515.121 | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 16.0.28625.61 | Consigliato
Microsoft.Component.CodeAnalysis.SDK | .NET Compiler Platform SDK | 16.2.29003.222 | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 16.5.29515.121 | Facoltativo
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 16.0.28315.86 | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | Nome | Versione
--- | --- | ---
Component.GitHub.VisualStudio | Estensione GitHub per Visual Studio | 2.5.9.5485
Component.Xamarin.Inspector | Xamarin Inspector | 16.0.28315.86
Component.Xamarin.Profiler | Xamarin Profiler | 16.0.28315.86
Component.Xamarin.Workbooks | Xamarin Workbooks | 16.0.28315.86
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 16.4.29409.204
Microsoft.Component.HelpViewer | Visualizzatore della Guida | 16.0.28625.61
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 16.4.29409.204
Microsoft.Net.Core.Component.SDK.2.2 | Runtime di .NET Core 2.2 (EOL).NET Core 2.2 Runtime (EOL) | 16.5.29813.82
Microsoft.Net.Core.Component.SDK.3.0 | Runtime di .NET Core 3.0 (EOL) | 16.5.29905.7
Microsoft.NetCore.ComponentGroup.DevelopmentTools.2.1 | Strumenti di sviluppo e .NET Core 2.1 | 16.3.29207.166
Microsoft.NetCore.ComponentGroup.Web.2.1 | Strumenti di sviluppo Web e .NET Core 2.1 | 16.3.29207.166
Microsoft.VisualStudio.Component.AzureDevOps.OfficeIntegration | Integrazione di Office con Azure DevOps | 16.0.28625.61
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | 16.0.28528.71
Microsoft.VisualStudio.Component.DependencyValidation.Community | Convalida delle dipendenze | 16.0.28517.75
Microsoft.VisualStudio.Component.Git | GIT per Windows | 16.0.28625.61
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | 16.0.28625.61
Microsoft.VisualStudio.Component.LinqToSql | Strumenti di LINQ to SQL | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.20) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | ATL C++ v14.20 per Build Tools v142 (x86 e x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | ATL C++ v14.20 per Build Tools v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | ATL C++ v14.20 per Build Tools v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | ATL C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | MFC C++ v14.20 per Build Tools v142 (x86 e x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | MFC C++ v14.20 per Build Tools v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | MFC C++ v14.20 per Build Tools v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | MFC C++ v14.20 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM VS 2019 C++ (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 - Librerie con mitigazione Spectre ARM64 VS 2019 C++ (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | ATL C++ v14.21 per Build Tools v142 (x86 e x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | ATL C++ v14.21 per Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | ATL C++ v14.21 per Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | ATL C++ v14.21 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | MFC C++ v14.21 per Build Tools v142 (x86 e x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | MFC C++ v14.21 per Build Tools v142 (ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | MFC C++ v14.21 per Build Tools v142 (ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | MFC C++ v14.21 per Build Tools v142 con mitigazioni Spectre (x86 e x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 - Librerie con mitigazione Spectre x64/x86 VS 2019 C++ (v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 - VS 2019 C++ Build Tools ARM (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | Librerie con mitigazione Spectre ARM MSVC v142 - VS 2019 C++ (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 - VS 2019 C++ Build Tools ARM64 (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | Librerie con mitigazione Spectre ARM64 MSVC v142 - VS 2019 C++ (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | ATL v14.22 di C'è per gli strumenti di compilazione v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | ATL v14.22 per gli strumenti di compilazione v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | ATL v14.22 per gli strumenti di compilazione v142 con Mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | ATL di c'è v14.22 per gli strumenti di compilazione v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | ATL v14.22 per gli strumenti di compilazione v142 con Mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | ATL v14.22 per gli strumenti di compilazione v142 con mitigazioni Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | Supporto C++/CLI per Build Tools v142 (14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC | MFC di C'è v14.22 per gli strumenti di compilazione v142 (x86 & x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | MFC di Visual C. V14.22 per gli strumenti di compilazione v142 (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | MFC di Visual E SV14.22 per la versione 142 con mitigazioni Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | MFC di Visual E N. V14.22 per gli strumenti di compilazione v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | MFC di Visual E N. V14.22 per la versione 142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | MFC di C'è v14.22 per gli strumenti di compilazione v142 con mitigazioni Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ Build Tools x64/x86 (v14.22) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | Librerie con mitigazione Spectre x64/x86 MSVC v142 - VS 2019 C++ (v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - Strumenti di compilazione ARM di VS 2019 C | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | Libs mitigate di MSVC v142 - VS 2019 C'è ARM Spectre -mitigato (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - Strumenti di compilazione di VS 2019 C'ARM64 (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | Libs mitigate di Spectre MSVC v142 (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | ATL v14.23 di C'è per gli strumenti di compilazione v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | ATL v14.23 per gli strumenti di compilazione v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | ATL v14.23 per gli strumenti di compilazione v142 con Mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | ATL di c'è v14.23 per gli strumenti di compilazione v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | ATL v14.23 per gli strumenti di compilazione v142 con Mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | ATL v14.23 di C'è per gli strumenti di compilazione v142 con mitigazioni Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | Supporto per gli strumenti di compilazione v142 (14.23) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.23.MFC | MFC di C'è v14.23 per gli strumenti di compilazione v142 (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | MFC di Visual C. V14.23 per gli strumenti di compilazione v142 (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | MFC di Visual E Versioni V14.23 per la versione 142 con mitigazioni Spectre (ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | MFC di Visual C. v14.23 per gli strumenti di compilazione v142 (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | MFC di Visual E N. V14.23 per gli strumenti di compilazione v142 con mitigazioni Spectre (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | MFC di Visual E N. V14.23 per gli strumenti di compilazione v142 con attenuazioni Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | Libs mitigate da MSVC v142 - VS 2019 C'x64/x86 Spectre (v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - Strumenti di compilazione ARM di VS 2019 C | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | LIBs mitigate di Spectre (v14.24) di CONFRONTO (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 - Strumenti di compilazione di VS 2019 C'ARM64 (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | Libs mitigate di Spectre MSVC v142 (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | ATL v14.24 di C'è per gli strumenti di compilazione v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | ATL di c'è v14.24 per gli strumenti di compilazione v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | ATL v14.24 di C'è v14.24 per gli strumenti di compilazione v142 con mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | ATL di c'è v14.24 per gli strumenti di compilazione v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | ATL v14.24 di C'è v14.24 per gli strumenti di compilazione v142 con mitigazioni Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | ATL v14.24 di C'è v14.24 per gli strumenti di compilazione v142 con mitigazioni Spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | Supporto per gli strumenti di compilazione v142 (14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC | MFC di C'è v14.24 per gli strumenti di compilazione v142 (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | MFC di Visual E N. V14.24 per gli strumenti di compilazione v142 (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | MFC di Visual E Versioni V14.24 per la versione 142 con mitigazioni Spectre (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | MFC di Visual E N. V14.24 per gli strumenti di compilazione v142 (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | MFC di Visual E N. V14.24 per la versione 142 con mitigazioni Spectre (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | MFC di C' v14.24 per gli strumenti di compilazione v142 con attenuazioni Spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 - Strumenti di compilazione MSVC v142 - VS 2019 C'x64/x86 (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | Libs mitigate di MSVC v142 - VS 2019 C'x64/x86 Spectre-mitigata (v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL di C'è per gli strumenti di compilazione v142 più recenti (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL per gli ultimi strumenti di compilazione v142 con Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL di C'è per gli strumenti di compilazione più recenti v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL per gli ultimi strumenti di compilazione v142 con Spectre Mitigations (ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL per gli ultimi strumenti di compilazione v142 con mitigazioni Spectre (x86 & x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC di C'è per gli strumenti di compilazione v142 più recenti con mitigazioni Spectre (x86 & x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC in C. per gli strumenti di compilazione v142 più recenti (ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC in C, per gli strumenti di compilazione più recenti della versione 142 con Spectre Mitigations (ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC in C. per gli ultimi strumenti di compilazione v142 (ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | MFC in C, per gli strumenti di compilazione v142 più recenti con Spectre Mitigations (ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | MSM di C++ 2019 Redistributable | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | LIBs mitigate di Spectre ARM (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Libs mitigate di Spectre MSVC v142 (v14.25) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Libs mitigate da MSVC v142 - VS 2019 C'x64/x86 Spectre (v14.25)  | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM VS 2017 C++ (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 - Librerie con mitigazione Spectre ARM64 VS 2017 C++ (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | ATL C++ per Build Tools v141 (x86 e x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | ATL C++ per Build Tools v141 (ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | ATL C++ per Build Tools v141 con mitigazioni Spectre (ARM) | 16.5.29721.120
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
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 - Librerie con mitigazione Spectre x64/x86 VS 2017 C++ (v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 16.0.28707.177
Microsoft.VisualStudio.Component.WinXP | Supporto di Windows XP C++ per strumenti VS 2017 (v141) [deprecato] | 16.1.28811.260
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 16.1.28810.153
