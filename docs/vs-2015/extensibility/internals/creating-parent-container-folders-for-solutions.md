---
title: Creazione di cartelle del contenitore padre per le soluzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196934"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Creazione di cartelle contenitore padre per le soluzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nel plug-in del controllo del codice sorgente versione 1,2, un utente può specificare una singola destinazione radice del controllo del codice sorgente per tutti i progetti Web all'interno della soluzione. Questa singola radice è denominata Super Unified root (SUR).  
  
 Nell'API del plug-in del controllo del codice sorgente versione 1,1, se l'utente ha aggiunto una soluzione multiprogetto al controllo del codice sorgente, all'utente viene richiesto di specificare una destinazione del controllo del codice sorgente per ogni progetto Web.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Funzioni nuove  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 L' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE crea quasi sempre una cartella sur quando si aggiunge una soluzione al controllo del codice sorgente. In particolare, questa operazione viene eseguita nei casi seguenti:  
  
- Il progetto è un progetto Web di condivisione file.  
  
- Sono presenti unità diverse per il progetto e il file di soluzione.  
  
- Sono disponibili condivisioni diverse per il progetto e il file di soluzione.  
  
- I progetti sono stati aggiunti separatamente (in una soluzione controllata dal codice sorgente).  
  
  In è [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consigliabile che il nome della cartella sur corrisponda al nome della soluzione senza estensione. Nella tabella seguente viene riepilogato il comportamento delle due versioni.  
  
|Feature|API del plug-in del controllo tSource versione 1,1|API del plug-in del controllo del codice sorgente versione 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Aggiungi soluzione a SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Aggiungi progetto a soluzione controllata dal codice sorgente|SccGetProjPath()<br /><br /> OpenProject ()|SccGetParentProjectPath()<br /><br /> SccOpenProject () **Nota:**  in Visual Studio si presuppone che una soluzione sia un figlio diretto di sur.|  
  
## <a name="examples"></a>Esempi  
 Nella tabella seguente sono elencati due esempi. In entrambi i casi, all' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utente viene richiesto di specificare un percorso di destinazione per la soluzione nel controllo del codice sorgente finché il  *user_choice* non viene specificato come destinazione. Quando si specifica il user_choice, la soluzione e due progetti vengono aggiunti senza richiedere all'utente le destinazioni del controllo del codice sorgente.  
  
|La soluzione contiene|Sui percorsi del disco|Struttura predefinita del database|  
|-----------------------|-----------------------|--------------------------------|  
|sln1. sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot $ \web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*/C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1. sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*/D/Web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 La cartella SUR e le sottocartelle vengono create indipendentemente dal fatto che l'operazione venga annullata o non riesca a causa di un errore. Non vengono rimosse automaticamente in condizioni di errore o di annullamento.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] il valore predefinito è il comportamento della versione 1,1 se il plug-in del controllo del codice sorgente non restituisce `SCC_CAP_CREATESUBPROJECT` e i `SCC_CAP_GETPARENTPROJECT` flag di funzionalità. Inoltre, gli utenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] possono scegliere di ripristinare il comportamento della versione 1,1 impostando il valore della chiave seguente su DWORD: 00000001:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = DWORD: 00000001  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
