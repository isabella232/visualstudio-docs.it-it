---
title: Compilazione e debug delle soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d0bc3185b0684f96bf31cc127cd852448afe772
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765070"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Compilare ed eseguire il debug di soluzioni SharePoint
  In generale, compilazione e debug delle soluzioni SharePoint è quella della compilazione e debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Gli argomenti di questa sezione illustrano le differenze esistenti.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Output del progetto per le soluzioni SharePoint
 Compilazione di soluzioni SharePoint crea un pacchetto della soluzione e assembly (*wsp*) file. Nella tabella seguente mostra i percorsi dei file durante una compilazione.  
  
|Elemento di compilazione|Cartella di output|  
|----------------|-------------------|  
|Assembly, database di programma (*PDB*), e *con estensione wsp* file.|*{ProjectName} \bin\debug* o *{ProjectName} \bin\Release.*|  
|File di elemento di progetto SharePoint.|*{ProjectName} \pkg\debug* o *\pkg\release {ProjectName}*|  
|Compilare i file intermedi.|*{ProjectName} \obj\debug* o *\obj\release {ProjectName}*|  
|File intermedi di pacchetto.|*{ProjectName} \pkgobj\debug* o *\pkgobj\release {ProjectName}*|  
  
## <a name="build-sharepoint-solutions"></a>Compilare soluzioni SharePoint
 Per compilare soluzioni SharePoint, il computer di sviluppo deve avere la versione corretta del server di SharePoint installato. In caso contrario, la creazione di soluzioni di SharePoint è lo stesso di quello di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [procedura: compilare soluzioni SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Eseguire il debug e testare le soluzioni SharePoint
 Prima del debug, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie il *wsp* pacchetto nel server SharePoint, viene attivato il sito e funzionalità con ambito Web e in alcuni casi, viene avviato il progetto. In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per ulteriori informazioni, vedere [risoluzione dei problemi delle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) e [debug delle soluzioni SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Eseguire il debug e verificare le soluzioni di SharePoint utilizzando le funzionalità ALM
 Con le funzionalità di Visual Studio ALM, ad esempio il testing unità e IntelliTrace, è possibile individuare con maggiore precisione i problemi delle soluzioni di SharePoint. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per ulteriori informazioni, vedere [verifica e debug del codice SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [profilatura delle prestazioni di applicazioni SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Per creare un pacchetto o distribuire soluzioni di SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] deve disporre dell'autorizzazione per copiare i file nel server SharePoint. È necessario eseguire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come un processo con privilegi elevato e l'utente account deve essere un amministratore della raccolta siti nel server SharePoint. Inoltre, è necessario specificare se il progetto è una soluzione creata mediante sandbox o una soluzione farm. Per ulteriori informazioni, vedere [le differenze tra creata mediante sandbox e soluzioni Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Uso del comando Pulisci  
 Quando una soluzione SharePoint viene installata in un server SharePoint per il debug, il **Pulisci** comando non Disinstalla la soluzione. In alternativa, è necessario disattivare le funzionalità tramite la configurazione di SharePoint.  
  
## <a name="see-also"></a>Vedere anche
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Esplorazione di connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 