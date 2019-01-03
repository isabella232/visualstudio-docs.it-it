---
title: Estensione SharePoint Packaging and Deployment | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54c735bf0ab534e042e595fd12864a06dcf0a30f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916879"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Estendere la distribuzione e creazione di pacchetti di SharePoint
  È possibile estendere il processo di creazione di pacchetti e distribuzione per i progetti SharePoint.
  
## <a name="create-deployment-steps"></a>Creare passaggi di distribuzione
 Per la distribuzione di un progetto SharePoint in [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] sono previste varie fasi. Visual Studio include fasi di distribuzione predefinite per molte attività, quali la ritrazione e l'aggiunta di soluzioni. È comunque possibile creare fasi di distribuzione personalizzate.  
  
 Per una procedura dettagliata viene illustrato come creare un passaggio di distribuzione, vedere [procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="create-deployment-configurations"></a>Creare le configurazioni di distribuzione
 Una configurazione di distribuzione è un set di fasi di distribuzione che viene eseguito per un determinato progetto, ma può influire su tutti gli elementi del progetto SharePoint. Tutte le configurazioni di distribuzione includono un set di passaggi eseguito quando viene distribuito il progetto e un altro set eseguito in caso di retrazione. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] include due configurazioni di distribuzione predefinite, ma è anche possibile creare una propria. Quando si crea una configurazione di distribuzione, è possibile includere fasi di distribuzione predefinite e fasi personalizzate.  
  
 Per una procedura dettagliata viene illustrato come creare una configurazione di distribuzione, vedere [procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Eseguire codice quando una soluzione di SharePoint viene distribuita o ritratto
 È possibile gestire gli eventi per eseguire attività aggiuntive quando una soluzione SharePoint viene distribuita o ritratta. Visual Studio genera eventi che è possibile gestire negli scenari seguenti:  
  
-   Prima e dopo l'esecuzione di ogni passaggio di distribuzione per un elemento di progetto SharePoint. Per altre informazioni, vedere [Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Prima e dopo che un progetto SharePoint viene distribuito o ritratto. Per altre informazioni, vedere [Procedura: Eseguire codice quando un progetto SharePoint viene distribuito o ritratto](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
## <a name="handle-deployment-conflicts"></a>Gestire i conflitti di distribuzione
 Alcuni tipi di elementi di progetto SharePoint, tra cui moduli, Web part, istanze di elenco e tipi di contenuto, forniscono la risoluzione incorporata dei conflitti di distribuzione. Quando si distribuisce una soluzione che contiene uno di questi elementi di progetto, Visual Studio verifica innanzitutto se esiste già un file nel sito di SharePoint con lo stesso nome, URL o ID come file nell'elemento che si sta distribuendo. Se si verifica un conflitto, Visual Studio è in grado di risolvere automaticamente il conflitto o di chiedere conferma all'utente per determinare se desidera risolvere il conflitto o annullare la distribuzione in Visual Studio. Per altre informazioni, vedere [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 È possibile estendere questa funzionalità fornendo codice personalizzato per la verifica e la risoluzione dei conflitti di distribuzione. Per altre informazioni, vedere [Procedura: Gestire i conflitti di distribuzione](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Eseguire le operazioni dalla riga di comando prima o dopo aver distribuito un progetto
 Se si desidera eseguire un'operazione della riga di comando quando si distribuisce una soluzione SharePoint, è possibile impostare le proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> di un oggetto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio esegue questi comandi prima e dopo la distribuzione del progetto.  
  
 In alcuni casi, possono verificarsi conflitti di distribuzione. Sono disponibili diversi modi per risolvere i conflitti. Per altre informazioni, vedere [risolvere i problemi di SharePoint e distribuzione di pacchetti](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="customize-validation-rules"></a>Personalizzare le regole di convalida
 Prima di distribuire un pacchetto di soluzioni (con estensione wsp), è possibile creare funzionalità personalizzate e regole di convalida del pacchetto per verificare che la funzionalità o il pacchetto siano validi. Ad esempio, è possibile segnalare informazioni, avvisi o errori per consentire agli sviluppatori di risolvere i problemi di convalida. Per altre informazioni, vedere [Procedura: Creare funzionalità personalizzate e un pacchetto le regole di convalida per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Eseguire codice quando vengono eseguiti i passaggi di distribuzione](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Procedura dettagliata: Creare un passaggio di distribuzione personalizzato per progetti SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Procedura: Creare pacchetti di funzionalità personalizzate le regole di convalida per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Estendere il sistema di progetto SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
