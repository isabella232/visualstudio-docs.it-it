---
title: Compilazione e debug delle soluzioni SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 0ab8fe8b7a6a26e855e603a2f2969c894ff7da50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987194"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Compilare ed eseguire il debug di soluzioni SharePoint
  In generale, la compilazione e debug delle soluzioni SharePoint è quello utilizzato per compilazione e debug di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Gli argomenti di questa sezione illustrano le differenze esistenti.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Output del progetto per le soluzioni SharePoint
 Creazione di soluzioni SharePoint consente di creare un pacchetto della soluzione e assembly (*wsp*) file. La tabella seguente illustra i percorsi dei file durante una compilazione.  
  
|Compilare l'elemento|Cartella di output|  
|----------------|-------------------|  
|Assembly, database di programma (*PDB*), e *wsp* file.|*\<Nome progetto > \bin\debug* oppure  *\<NomeProgetto > \bin\Release.*|  
|File di elemento di progetto SharePoint.|*\<Nome progetto > \pkg\debug* oppure  *\<NomeProgetto > \pkg\release*|  
|Compilare i file intermedi.|*\<Nome progetto > \obj\debug* oppure  *\<NomeProgetto > \obj\release*|  
|File intermedi del pacchetto.|*\<Nome progetto > \pkgobj\debug* oppure  *\<NomeProgetto > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Compilare soluzioni SharePoint
 Per compilare soluzioni SharePoint, il computer di sviluppo deve avere la versione corretta di SharePoint server sono installati. In caso contrario, la creazione di soluzioni di SharePoint è quello utilizzato per la creazione di altri tipi di progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Per altre informazioni, vedere [Procedura: Compilare soluzioni SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Eseguire il debug e testare le soluzioni SharePoint
 Prima del debug, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] copie di *wsp* pacchetto nel server SharePoint, attiva il sito e le funzionalità con ambito Web e in alcuni casi, viene avviato il progetto. In altri casi, potrebbe essere necessario aprire manualmente il progetto. Per altre informazioni, vedere [soluzioni di risolvere i problemi di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) e [soluzioni SharePoint Debug](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Eseguire il debug e verificare le soluzioni di SharePoint usando le funzionalità di servizi di Azure DevOps
 Funzionalità di DevOps servizi Azure, ad esempio gli unit test e IntelliTrace consentono più accuratamente individuare i problemi delle soluzioni di SharePoint. Con la profilatura è possibile individuare e identificare aree problematiche delle prestazioni nelle soluzioni di SharePoint. Per altre informazioni, vedere [verifica e debug del codice SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [profilatura delle prestazioni di applicazioni SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Per creare un pacchetto o distribuire soluzioni di SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] deve disporre dell'autorizzazione per copiare i file nel server SharePoint. È necessario eseguire [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come un processo con privilegi elevati e l'utente account deve essere un amministratore di raccolte di sito nel server SharePoint. Inoltre, è necessario specificare se il progetto è una soluzione creata mediante sandbox o una soluzione farm. Per altre informazioni, vedere [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Uso del comando Pulisci  
 Quando si installa una soluzione di SharePoint in un server SharePoint per il debug, il **Pulisci** comando consente di disinstallare la soluzione. In alternativa, è necessario disattivare le funzionalità tramite la configurazione di SharePoint.  
  
## <a name="see-also"></a>Vedere anche
 [Lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Esplorare le connessioni di SharePoint tramite Esplora Server](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
