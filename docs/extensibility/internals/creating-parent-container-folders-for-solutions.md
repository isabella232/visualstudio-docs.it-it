---
title: Creazione di cartelle contenitore padre per le soluzioni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9b48cb7862b23df325b35bba0cb3e197573e3c0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102718"
---
# <a name="create-parent-container-folders-for-solutions"></a>Creare cartelle dei contenitori per le soluzioni padre
Origine controllo plug-in API versione 1.2, un utente può specificare una destinazione di controllo di origine solo nodo radice per tutti i progetti web all'interno della soluzione. Questa singola radice viene chiamata una radice unificata con privilegi elevati (SUR).

 Origine controllo plug-in API versione 1.1, se l'utente aggiunto una soluzione multiprogetto al controllo del codice sorgente, l'utente è stato richiesto di specificare una destinazione di controllo di origine per ciascun progetto web.

## <a name="new-capability-flags"></a>Nuovi flag funzionalità
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nuove funzioni
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE crea una cartella SUR quasi sempre quando si aggiunge una soluzione a controllo del codice sorgente. In particolare, esegue l'operazione nei casi seguenti:

- Il progetto è un progetto web di condivisione file.

- Esistono unità differenti per il progetto e il file della soluzione.

- Esistono diverse quote per il progetto e il file della soluzione.

- I progetti sono stati aggiunti separatamente (in una soluzione di controllo del codice sorgente).

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è consigliabile che il nome della cartella SUR coincidere con il nome della soluzione senza l'estensione. La tabella seguente riepiloga il comportamento in due versioni.

|Funzionalità|API del plug-in versione 1.1 di controllo del codice sorgente|Versione 1.2 dell'API del plug-in controllo del codice sorgente|
|-------------| - | - |
|Aggiungi soluzione al controllo del codice sorgente|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Aggiungi progetto alla soluzione di controllo del codice sorgente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:**  Visual Studio presuppone che una soluzione è un figlio diretto del sur la.|

## <a name="examples"></a>Esempi
 Nella tabella seguente sono elencati due esempi. In entrambi i casi, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utente viene richiesto un percorso di destinazione per la soluzione nel controllo del codice sorgente finché il *user_choice* viene specificato come destinazione. Quando viene specificato il user_choice, senza chiedere conferma all'utente per le destinazioni di controllo di origine vengono aggiunti alla soluzione e due progetti.

|Soluzione contiene|In percorsi su disco|Struttura del database predefinito|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/C/Web1<br /><br /> $/ < user_choice > / Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/ < user_choice > / sln1<br /><br /> $/ < user_choice >/D/web1<br /><br /> $/ < user_choice >/sln1/win1|

 La cartella SUR e sottocartelle vengono create indipendentemente dal fatto che l'operazione è stata annullata o ha esito negativo a causa di un errore. Essi non vengono rimossi automaticamente in condizioni di errore o annullamento.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Per impostazione predefinita al comportamento versione 1.1 se il plug-in del controllo del codice sorgente non viene restituito `SCC_CAP_CREATESUBPROJECT` e `SCC_CAP_GETPARENTPROJECT` i flag funzionalità. Inoltre, gli utenti del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può scegliere di ripristinare il comportamento della versione 1.1 impostando il valore della chiave seguente *dword:00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl** = *dword:00000001*

## <a name="see-also"></a>Vedere anche
- [Novità di plug-in origine controllo API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)