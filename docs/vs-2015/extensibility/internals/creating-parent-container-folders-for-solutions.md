---
title: Creazione di cartelle contenitore padre per le soluzioni | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196934"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Creazione di cartelle contenitore padre per le soluzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nell'API versione 1.2 del plug-in controllo di origine, un utente può specificare una destinazione di controllo di origine solo nodo radice per tutti i progetti Web all'interno della soluzione. Questa singola radice viene chiamata una radice unificata con privilegi elevati (SUR).  
  
 Nell'API versione 1.1 del plug-in controllo di origine, se l'utente aggiunto una soluzione multiprogetto al controllo del codice sorgente, l'utente è stato richiesto di specificare una destinazione di controllo di origine per ciascun progetto Web.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE crea una cartella SUR quasi sempre quando si aggiunge una soluzione a controllo del codice sorgente. In particolare, esegue l'operazione nei casi seguenti:  
  
- Il progetto è una condivisione file di progetto Web.  
  
- Esistono unità differenti per il progetto e il file della soluzione.  
  
- Esistono diverse quote per il progetto e il file della soluzione.  
  
- I progetti sono stati aggiunti separatamente (in una soluzione di controllo del codice sorgente).  
  
  In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è consigliabile che il nome della cartella SUR coincidere con il nome della soluzione senza l'estensione. La tabella seguente riepiloga il comportamento in due versioni.  
  
|Funzionalità|tSource controllo plug-in API versione 1.1|Versione 1.2 dell'API del plug-in controllo del codice sorgente|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Aggiungi soluzione al controllo del codice sorgente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|  
|Aggiungi progetto alla soluzione di controllo del codice sorgente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject() **Note:**  Visual Studio presuppone che una soluzione è un figlio diretto del sur la.|  
  
## <a name="examples"></a>Esempi  
 Nella tabella seguente sono elencati due esempi. In entrambi i casi, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utente viene richiesto un percorso di destinazione per la soluzione nel controllo del codice sorgente finché il *user_choice* viene specificato come destinazione. Quando viene specificato il user_choice, senza chiedere conferma all'utente per le destinazioni di controllo di origine vengono aggiunti alla soluzione e due progetti.  
  
|Soluzione contiene|In percorsi su disco|Struttura del database predefinito|  
|-----------------------|-----------------------|--------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> WEB2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\server\wwwroot$\web2|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /C/Web1<br /><br /> $/*user_choice*/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/sln1<br /><br /> $/*user_choice*  /D/web1<br /><br /> $/*user_choice*/sln1/win1|  
  
 La cartella SUR e sottocartelle vengono create indipendentemente dal fatto che l'operazione è stata annullata o ha esito negativo a causa di un errore. Essi non vengono rimossi automaticamente in condizioni di errore o annullamento.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Per impostazione predefinita al comportamento versione 1.1 se il plug-in del controllo del codice sorgente non viene restituito `SCC_CAP_CREATESUBPROJECT` e `SCC_CAP_GETPARENTPROJECT` i flag funzionalità. Inoltre, gli utenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] può scegliere di ripristinare il comportamento della versione 1.1 impostando il valore della seguente chiave per dword:00000001:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
