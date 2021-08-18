---
title: Compilazione e debug SharePoint soluzioni | Microsoft Docs
description: Informazioni su come compilare ed eseguire il debug SharePoint soluzioni e capire in che modo è diverso dalla compilazione e dal debug di altri tipi di progetti in Visual Studio.
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
ms.openlocfilehash: 8da574fb42e9a34bef81bd6690861141cfeec941
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027214"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Build e debug delle soluzioni SharePoint
  In generale, la compilazione e il debug SharePoint soluzioni sono le stesse della compilazione e del debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Gli argomenti di questa sezione illustrano le differenze esistenti.

## <a name="project-output-for-sharepoint-solutions"></a>Project output per SharePoint soluzioni
 La compilazione SharePoint soluzioni crea assembly e un file del pacchetto della soluzione *(con estensione wsp).* La tabella seguente illustra i percorsi di questi file durante una compilazione.

|Elemento di compilazione|Cartella di output|
|----------------|-------------------|
|File di assembly, database di programma *(con estensione pdb)* *e wsp.*|*\<ProjectName> \bin\debug* o *\<ProjectName> \bin\release*|
|SharePoint file dell'elemento di progetto.|*\<ProjectName> \pkg\debug* o *\<ProjectName> \pkg\release*|
|Compilare file intermedi.|*\<ProjectName> \obj\debug* o *\<ProjectName> \obj\release*|
|File intermedi del pacchetto.|*\<ProjectName> \pkgobj\debug* o *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Creare SharePoint soluzioni
 Per compilare SharePoint, nel computer di sviluppo deve essere installata la versione corretta SharePoint server. In caso contrario, SharePoint soluzioni di compilazione è uguale alla compilazione di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, vedere [Procedura: Compilare SharePoint soluzioni](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Eseguire il debug e il test SharePoint soluzioni
 Prima del debug, copia il pacchetto con estensione wsp nel server SharePoint, attiva le funzionalità del sito e con ambito Web e, in alcuni [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] casi, avvia il progetto.  In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per altre informazioni, vedere [Risolvere i problemi SharePoint soluzioni e](../sharepoint/troubleshooting-sharepoint-solutions.md) Debug SharePoint [soluzioni](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Eseguire il debug e verificare SharePoint soluzioni usando Azure DevOps Services funzionalità
 Azure DevOps Services funzionalità quali unit test e IntelliTrace consentono di individuare in modo più accurato i problemi nelle SharePoint soluzioni. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per altre informazioni, vedere [Verifying and Debugging SharePoint Code](../sharepoint/verifying-and-debugging-sharepoint-code.md) and [Profiling the Performance of SharePoint Applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Per creare un pacchetto o distribuire SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] è necessario disporre dell'autorizzazione per copiare i file SharePoint server. È necessario eseguire come processo con privilegi elevati e l'account utente deve essere un amministratore delle raccolte siti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nel server SharePoint server. È anche necessario specificare se il progetto è una soluzione in modalità sandbox o una soluzione farm. Per altre informazioni, vedere [Differenze tra soluzioni in modalità sandbox e soluzioni farm.](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)

## <a name="using-the-clean-command"></a>Uso del comando Clean
 Quando una SharePoint viene installata in un server SharePoint per il debug, il **comando Pulisci** non disinstalla la soluzione. È invece necessario disattivare le funzionalità tramite la SharePoint configurazione.

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Esplorare SharePoint connessioni usando Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
