---
title: Compilazione e debug di soluzioni SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016360"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Build e debug delle soluzioni SharePoint
  In generale, la compilazione e il debug di soluzioni SharePoint equivale alla compilazione e al debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Gli argomenti di questa sezione illustrano le differenze esistenti.

## <a name="project-output-for-sharepoint-solutions"></a>Output del progetto per le soluzioni SharePoint
 La compilazione di soluzioni SharePoint crea assembly e un file di pacchetto di soluzione (con*estensione wsp*). Nella tabella seguente vengono illustrati i percorsi di questi file durante una compilazione.

|Elemento di compilazione|Cartella di output|
|----------------|-------------------|
|Assembly, database di programma (*PDB*) e file con *estensione wsp* .|* \<ProjectName> \bin\Debug* o * \<ProjectName> \bin\Release*|
|File degli elementi del progetto SharePoint.|* \<ProjectName> \pkg\debug* o * \<ProjectName> \pkg\release*|
|Compila i file intermedi.|* \<ProjectName> \obj\debug* o * \<ProjectName> \obj\release*|
|File intermedi del pacchetto.|* \<ProjectName> \pkgobj\debug* o * \<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Compila soluzioni SharePoint
 Per compilare soluzioni SharePoint, nel computer di sviluppo deve essere installata la versione corretta di SharePoint Server. In caso contrario, la compilazione di soluzioni SharePoint equivale alla compilazione di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Per altre informazioni, vedere [procedura: compilare soluzioni SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Eseguire il debug e testare le soluzioni SharePoint
 Prima di eseguire il debug, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia il pacchetto con estensione *WSP* nel server SharePoint, attiva il sito e le funzionalità con ambito Web e, in alcuni casi, avvia il progetto. In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per ulteriori informazioni, vedere [risoluzione dei problemi relativi](../sharepoint/troubleshooting-sharepoint-solutions.md) alle soluzioni SharePoint e [debug di soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Eseguire il debug e verificare le soluzioni SharePoint usando le funzionalità di Azure DevOps Services
 Azure DevOps Services funzionalità, ad esempio unit test e IntelliTrace, consentono di individuare con maggiore precisione i problemi delle soluzioni di SharePoint. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per ulteriori informazioni, vedere [Verifica e debug del codice SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [profiling delle prestazioni delle applicazioni SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Per creare un pacchetto o distribuire le soluzioni SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] è necessario disporre dell'autorizzazione per la copia dei file nel server SharePoint. È necessario eseguire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come processo con privilegi elevati e l'account utente deve essere un amministratore di raccolte siti nel server SharePoint. Inoltre, è necessario specificare se il progetto è una soluzione in modalità sandbox o una soluzione farm. Per altre informazioni, vedere [differenze tra le soluzioni in modalità sandbox e farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Uso del comando Pulisci
 Quando una soluzione SharePoint viene installata in un server SharePoint per il debug, il comando **Pulisci** non disinstalla la soluzione. Al contrario, è necessario disattivare le funzionalità tramite la configurazione di SharePoint.

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Esplorazione delle connessioni di SharePoint tramite Esplora server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
