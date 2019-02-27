---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Desktop Express 2017
titleSuffix: ''
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.workload:
- multiple
ms.openlocfilehash: 5f2c12201adebf148703083b825e98b35bbff7c1
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842494"
---
# <a name="visual-studio-2017-desktop-express-component-directory"></a>Elenco dei componenti di Visual Studio 2017 Desktop Express

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando o che è possibile specificare come dipendenza in un manifesto VSIX. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro.
* È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata anche aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Quando si impostano le dipendenze nel manifesto VSIX, è necessario specificare solo gli ID dei componenti. Usare le tabelle in questa pagina per determinare le dipendenze minime dei componenti. In alcuni scenari, ciò potrebbe portare alla specifica di un solo componente da un carico di lavoro. In altri scenari è possibile che vengano specificati più componenti da un singolo carico di lavoro o più componenti da più carichi di lavoro. Per altre informazioni, vedere la pagina [ Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="express-for-windows-desktop"></a>Express per Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**Descrizione:** consente di compilare applicazioni native e gestite come WPF, WinForms e Win32 con funzionalità di modifica del codice con riconoscimento della sintassi, controllo del codice sorgente e gestione degli elementi di lavoro. Include il supporto per C#, Visual Basic e Visual C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | 15.8.27825.0 | Obbligatorio
Microsoft.Component.HelpViewer | Help Viewer | 15.6.27323.2 | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | Obbligatorio
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | 15.8.27825.0 | Obbligatorio
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | 15.9.28107.0 | Obbligatorio
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | 15.8.27729.1 | Obbligatorio
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | 15.9.28016.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | 15.8.27729.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | 15.0.26621.2 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | 15.7.27617.1 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.6.27309.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | 15.8.27825.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Compilatori e librerie di Visual C++ per ARM64 | 15.9.28230.55 | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.8.27924.0 | Obbligatorio

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | nome | Versione
--- | --- | ---
N/D | N/D | N/D

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
