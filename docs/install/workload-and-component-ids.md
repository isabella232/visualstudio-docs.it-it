---
title: ID dei carichi di lavoro e dei componenti di Visual Studio
titleSuffix: ''
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 03/02/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.custom: seodec18
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b96088a2107ae826067287aee9f306aa0f590329
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324039"
---
# <a name="visual-studio-workload-and-component-ids"></a>ID dei carichi di lavoro e dei componenti di Visual Studio

Fare clic sui nomi delle edizioni riportati nella tabella seguente per visualizzare gli ID dei carichi di lavoro e dei componenti disponibili necessari per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX.

::: moniker range="vs-2017"

**Aggiornato per la [versione 15.9](/visualstudio/releasenotes/vs2017-relnotes/)**

| **Edizione** | **ID** | **Descrizione** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md?vs-2017) | Microsoft.VisualStudio.Product.Enterprise | Soluzione Microsoft DevOps per la produttività e il coordinamento in team di qualsiasi dimensione |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md?vs-2017) | Microsoft.VisualStudio.Product.Professional | Servizi e strumenti di sviluppo professionali per team di piccole dimensioni |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | IDE completo e gratuito per studenti, sviluppatori singoli e open source |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2017](workload-component-id-vs-team-explorer.md?vs-2017) | Microsoft.VisualStudio.Product.TeamExplorer | Consente di interagire con Team Foundation Server e Azure DevOps Services senza usare un set di strumenti di sviluppo di Visual Studio |
| [Visual Studio Desktop Express 2017](workload-component-id-vs-express.md?vs-2017) | Microsoft.VisualStudio.Product.WDExpress | Sviluppare applicazioni native e gestite come WPF, WinForms e Win32 con funzionalità di modifica del codice con riconoscimento della sintassi, controllo del codice sorgente e gestione degli elementi di lavoro. Include il supporto per C#, Visual Basic e Visual C++. |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2017](workload-component-id-vs-build-tools.md?vs-2017) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools consente di creare applicazioni native e gestite basate su MSBuild senza l'IDE di Visual Studio. Sono disponibili opzioni per installare le librerie e i compilatori Visual C++, MFC, ATL e il supporto C++/CLI. |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2017](workload-component-id-vs-test-agent.md?vs-2017)  | Microsoft.VisualStudio.Product.TestAgent | Supporta l'esecuzione di test automatizzati e test di carico in remoto |
| [Visual&nbsp;Studio Test&nbsp;Controller 2017](workload-component-id-vs-test-controller.md?vs-2017) | Microsoft.VisualStudio.Product.TestController | Consente di distribuire i test automatizzati in più computer |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md?vs-2017) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md?vs-2017) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

Per altre informazioni su come usare questi elenchi, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) e la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2017).

::: moniker-end

::: moniker range="vs-2019"

**Aggiornato per [Visual Studio 2019 RC](/visualstudio/releases/2019/release-notes/)**

| **Edizione** | **ID** | **Descrizione** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2019](workload-component-id-vs-enterprise.md?vs-2019) | Microsoft.VisualStudio.Product.Enterprise | Soluzione Microsoft DevOps per la produttività e il coordinamento in team di qualsiasi dimensione |
| [Visual&nbsp;Studio Professional&nbsp;2019](workload-component-id-vs-professional.md?vs-2019) | Microsoft.VisualStudio.Product.Professional | Servizi e strumenti di sviluppo professionali per team di piccole dimensioni |
| [Visual&nbsp;Studio Community&nbsp;2019](workload-component-id-vs-community.md?vs-2019) | Microsoft.VisualStudio.Product.Community | IDE completo e gratuito per studenti, sviluppatori singoli e open source |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2019](workload-component-id-vs-team-explorer.md?vs-2019) | Microsoft.VisualStudio.Product.TeamExplorer | Consente di interagire con Team Foundation Server e Azure DevOps Services senza usare un set di strumenti di sviluppo di Visual Studio |
| [Visual&nbsp;Studio Build&nbsp;Tools&nbsp;2019](workload-component-id-vs-build-tools.md?vs-2019) | Microsoft.VisualStudio.Product.BuildTools | Visual Studio Build Tools consente di creare applicazioni native e gestite basate su MSBuild senza l'IDE di Visual Studio. Sono disponibili opzioni per installare le librerie e i compilatori Visual C++, MFC, ATL e il supporto C++/CLI. |
| [Visual&nbsp;Studio Test&nbsp;Agent&nbsp;2019](workload-component-id-vs-test-agent.md?vs-2019)  | Microsoft.VisualStudio.Product.TestAgent | Supporta l'esecuzione di test automatizzati e test di carico in remoto |
| [Visual&nbsp;Studio Load&nbsp;Test&nbsp;Controller 2019](workload-component-id-vs-test-controller.md?vs-2019) | Microsoft.VisualStudio.Product.TestController | Consente di distribuire i test automatizzati in più computer |

Per altre informazioni su come usare questi elenchi, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) e la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2019).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Guida dell'amministratore di Visual Studio per Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
