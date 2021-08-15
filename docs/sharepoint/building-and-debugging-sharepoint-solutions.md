---
title: Compilazione e debug SharePoint soluzioni | Microsoft Docs
description: Informazioni su come compilare ed eseguire il debug SharePoint soluzioni e comprendere la differenza rispetto alla compilazione e al debug di altri tipi di progetti in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 38a82d6b5eba33bd3c832e0c028054087db17e107e1b93d2c1b173657d4a6bb4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244576"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Build e debug delle soluzioni SharePoint
  In generale, la compilazione e il debug SharePoint soluzioni è uguale alla compilazione e al debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Gli argomenti di questa sezione illustrano le differenze esistenti.

## <a name="project-output-for-sharepoint-solutions"></a>Project output per SharePoint soluzioni
 La SharePoint soluzioni crea assembly e un file di pacchetto della soluzione (*con estensione wsp).* La tabella seguente illustra i percorsi di questi file durante una compilazione.

|Elemento di compilazione|Cartella di output|
|----------------|-------------------|
|Assembly, database di programma (*file con estensione pdb*) e *wsp.*|*\<ProjectName> \bin\debug* o *\<ProjectName> \bin\release*|
|SharePoint file di elemento di progetto.|*\<ProjectName> \pkg\debug* o *\<ProjectName> \pkg\release*|
|Compilare file intermedi.|*\<ProjectName> \obj\debug* o *\<ProjectName> \obj\release*|
|Creare un pacchetto di file intermedi.|*\<ProjectName> \pkgobj\debug* o *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Compilare SharePoint soluzioni
 Per compilare SharePoint, nel computer di sviluppo deve essere installata la versione corretta SharePoint server. In caso contrario, SharePoint soluzioni è uguale alla compilazione di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, vedere [Procedura: Compilare SharePoint soluzioni](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Eseguire il debug e testare SharePoint soluzioni
 Prima del debug, copia il pacchetto con estensione wsp nel server SharePoint, attiva le funzionalità con ambito Sito e Web e, in alcuni casi, avvia [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto.  In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per altre informazioni, vedere [Risolvere i SharePoint soluzioni e](../sharepoint/troubleshooting-sharepoint-solutions.md) Eseguire il debug SharePoint [soluzioni](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Eseguire il debug e verificare SharePoint soluzioni usando Azure DevOps Services funzionalità
 Azure DevOps Services funzionalità quali unit test e IntelliTrace consentono di individuare in modo più accurato i problemi nelle SharePoint soluzioni. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per altre informazioni, vedere [Verifying and Debugging SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) and [Profiling the Performance of SharePoint Applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Per creare un pacchetto o distribuire SharePoint soluzioni, è necessario disporre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dell'autorizzazione per copiare file SharePoint server. È necessario eseguire come processo con privilegi elevati e l'account utente deve essere un amministratore delle raccolte siti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nel server SharePoint sito. È inoltre necessario specificare se il progetto è una soluzione in modalità sandbox o una soluzione farm. Per altre informazioni, vedere [Differenze tra soluzioni in modalità sandbox e farm.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)

## <a name="using-the-clean-command"></a>Uso del comando Clean
 Quando una SharePoint viene installata in un server SharePoint per il debug, il **comando Pulisci** non disinstalla la soluzione. È invece necessario disattivare le funzionalità tramite la SharePoint configurazione.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Esplorare SharePoint connessioni con Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
