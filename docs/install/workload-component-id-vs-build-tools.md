---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017
description: Usare gli ID dei carichi di lavoro e dei componenti di Visual Studio per creare applicazioni basate su Windows classiche
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 61c07c92f751a768451414e6bef876cbc22ec962
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281251"
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Elenco dei componenti di Visual Studio Build Tools 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando o che è possibile specificare come dipendenza in un manifesto VSIX. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro.
* È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Quando si impostano le dipendenze nel manifesto VSIX, è necessario specificare solo gli ID dei componenti. Usare le tabelle in questa pagina per determinare le dipendenze minime dei componenti. In alcuni scenari, ciò potrebbe portare alla specifica di un solo componente da un carico di lavoro. In altri scenari è possibile che vengano specificati più componenti da un singolo carico di lavoro o più componenti da più carichi di lavoro. Per altre informazioni, vedere la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="azure-development-build-tools"></a>Strumenti di compilazione sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.AzureBuildTools

**Descrizione:** attività e destinazioni di MSBuild per compilare applicazioni Azure.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.7.27520.0 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Strumenti di compilazione di Servizi cloud di Azure | 15.7.27617.1 | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Strumenti di sviluppo contenitori - Strumenti di compilazione | 15.7.27617.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo WCF | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo Web | 15.7.27604.0 | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Consigliato
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 15.7.27625.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Consigliato
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.6.27406.0 | Facoltativo

## <a name="net-desktop-build-tools"></a>Strumenti di compilazione desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**Descrizione:** strumenti per la creazione di applicazioni WPF, Windows Form e console con C#, Visual Basic e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.Component.ClickOnce.MSBuild | Strumenti di compilazione di ClickOnce | 15.7.27617.1 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Consigliato
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.TestTools.BuildTools | Funzionalità di base degli strumenti di test - Strumenti di compilazione | 15.7.27625.0 | Consigliato
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo WCF | 15.6.27309.0 | Consigliato
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# (compilatore) | 15.7.27604.0 | Facoltativo

## <a name="msbuild-tools"></a>Strumenti MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descrizione:** fornisce gli strumenti necessari per creare applicazioni basate su MSBuild.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.VisualStudio.Component.CoreBuildTools | Funzionalità di base di Visual Studio Build Tools | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio

## <a name="net-core-build-tools"></a>Strumenti di compilazione .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Descrizione:** strumenti per la creazione di applicazioni con .NET Core, ASP.NET Core, HTML/JavaScript e contenitori.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Obbligatorio
Microsoft.NetCore.BuildTools.ComponentGroup | Strumenti di compilazione .NET Core | 15.7.27617.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facoltativo

## <a name="nodejs-build-tools"></a>Strumenti di compilazione Node.js

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Supporto per Node.js | 15.6.27406.0 | Obbligatorio

## <a name="officesharepoint-build-tools"></a>Strumenti di compilazione Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**Descrizione:** consentono di creare componenti aggiuntivi per Office e SharePoint, nonché componenti aggiuntivi VSTO.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | Strumenti di compilazione di ClickOnce | 15.7.27617.1 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.7.27520.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Strumenti di compilazione sviluppo Office/SharePoint | 15.7.27617.1 | Obbligatorio
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo WCF | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo Web | 15.7.27604.0 | Obbligatorio
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Strumenti di compilazione di Visual Studio Tools per Office (VSTO) | 15.7.27617.1 | Consigliato
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.6.27406.0 | Facoltativo

## <a name="universal-windows-platform-build-tools"></a>Strumenti di compilazione per la piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**Descrizione:** fornisce gli strumenti necessari per compilare applicazioni per la piattaforma UWP (Universal Windows Platform).

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Obbligatorio
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Strumenti VC++ 2017 versione 14.14 di Visual Studio 15.7 aggiornata alla versione più recente 141 | 15.7.27625.0 | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | Prerequisiti di compilazione per la piattaforma UWP (Universal Windows Platform) | 15.7.27703.1 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Facoltativo

## <a name="visual-c-build-tools"></a>Strumenti di compilazione Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Descrizione:** Consente di compilare applicazioni desktop di Windows usando il set di strumenti Microsoft C++, ATL o MFC.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Funzionalità di base per Visual C++ Build Tools | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Aggiornamento di Visual C++ 2017 Redistributable | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Strumenti VC++ 2017 versione 14.14 di Visual Studio 15.7 aggiornata alla versione più recente 141 | 15.7.27625.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.TestTools.BuildTools | Funzionalità di base degli strumenti di test - Strumenti di compilazione | 15.7.27625.0 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 14.00 (v140) per desktop | 15.7.27617.1 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | ATL Visual C++ per x86 e x64 | 15.7.27625.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC Visual C++ per x86 e x64 | 15.7.27625.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli per la libreria standard (sperimentale) | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilatori e librerie di Visual C++ per ARM64 | 15.6.27309.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) per desktop C++ [x86 e x64] | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Windows 10 SDK (10.0.15063.0) per la piattaforma UWP: C++ | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) per desktop C++ [x86 e x64] | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C#, VB, JS | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Windows 10 SDK (10.0.16299.0) per la piattaforma UWP: C++ | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.Component.WinXP | Supporto Windows XP per C++ | 15.7.27703.1 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | 15.6.27406.0 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Supporto Windows XP per C++ | 15.7.27703.1 | Facoltativo

## <a name="web-development-build-tools"></a>Strumenti di compilazione sviluppo Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descrizione:** attività e destinazioni di MSBuild per compilare applicazioni Web.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.7.27520.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo Web | 15.7.27604.0 | Obbligatorio
Microsoft.Component.ClickOnce.MSBuild | Strumenti di compilazione di ClickOnce | 15.7.27617.1 | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Consigliato
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 2.0 | 15.6.27406.0 | Consigliato
Microsoft.VisualStudio.Component.AspNet45 | Funzionalità avanzate di ASP.NET | 15.7.27625.0 | Consigliato
Microsoft.VisualStudio.Component.DockerTools.BuildTools | Strumenti di sviluppo contenitori - Strumenti di compilazione | 15.7.27617.1 | Consigliato
Microsoft.VisualStudio.Component.TestTools.BuildTools | Funzionalità di base degli strumenti di test - Strumenti di compilazione | 15.7.27625.0 | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | Consigliato
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo WCF | 15.6.27309.0 | Consigliato
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Facoltativo
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7.1 | 15.6.27406.0 | Facoltativo
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.7 | 15.6.27406.0 | Facoltativo
Microsoft.Net.Core.Component.SDK.1x | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | 15.6.27406.0 | Facoltativo

## <a name="mobile-development-with-net"></a>Sviluppo di app per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**Descrizione:** strumenti per la creazione di applicazioni multipiattaforma per iOS, Android e Windows con C# e F#.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet.BuildTools | Destinazioni e attività di compilazione NuGet | 15.0.26919.1 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | Consigliato
Component.Android.SDK25 | Programma di installazione di Android SDK (livello API 25) | 15.6.27413.0 | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27520.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | ATL Visual C++ per ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | ATL Visual C++ per ARM con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ATL Visual C++ per ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | ATL Visual C++ per ARM64 con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | ATL Visual C++ (x86/x64) con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | MFC Visual C++ per x86/x64 con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (sperimentale) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | MFC Visual C++ per ARM | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | MFC Visual C++ per ARM con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | MFC Visual C++ per ARM64 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Supporto MFC Visual C++ per ARM64 con mitigazioni Spectre | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Librerie VC++ 2017 versione 14.14 di Visual Studio 15.7 per Spectre (ARM) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Librerie VC++ 2017 versione 14.14 di Visual Studio 15.7 per Spectre (ARM64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Librerie VC++ 2017 versione 14.14 di Visual Studio 15.7 per Spectre (x86 e x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Set di strumenti di VC++ 2017 versione 14.11 di Visual Studio 15.4 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | Set di strumenti di VC++ 2017 versione 14.12 di Visual Studio 15.5 | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | Set di strumenti di VC++ 2017 versione 14.13 di Visual Studio 15.6 | 15.0.27625.0

## <a name="get-support"></a>Supporto

Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:

* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto e trovare una risposta nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/).
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio). Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche

* [Build Tools per Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017#build-tools-for-visual-studio-2017)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
