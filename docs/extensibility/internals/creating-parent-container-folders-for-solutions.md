---
title: Creazione di cartelle contenitore padre per soluzioni | Microsoft Docs
description: Informazioni su come usare l'API plug-in del controllo del codice sorgente versione 1.2 per specificare una singola destinazione del controllo del codice sorgente radice per tutti i progetti Web all'interno di una soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 88ae7686af37b601ef6c5093a035d58281f2bdca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086703"
---
# <a name="create-parent-container-folders-for-solutions"></a>Creare cartelle contenitore padre per le soluzioni
Nell'API plug-in del controllo del codice sorgente versione 1.2 un utente può specificare una singola destinazione del controllo del codice sorgente radice per tutti i progetti Web all'interno della soluzione. Questa singola radice è denominata Super Unified Root (SUR).

 Nell'API plug-in del controllo del codice sorgente versione 1.1, se l'utente ha aggiunto una soluzione multiprogetto al controllo del codice sorgente, all'utente viene richiesto di specificare una destinazione del controllo del codice sorgente per ogni progetto Web.

## <a name="new-capability-flags"></a>Nuovi flag di funzionalità
 `SCC_CAP_CREATESUBPROJECT`

 `SCC_CAP_GETPARENTPROJECT`

## <a name="new-functions"></a>Nuove funzioni
- [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)

- [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'IDE crea quasi sempre una cartella SUR quando si aggiunge una soluzione al controllo del codice sorgente. In particolare, esegue questa operazione nei casi seguenti:

- Il progetto è un progetto Web di condivisione file.

- Sono disponibili unità diverse per il progetto e il file di soluzione.

- Sono disponibili condivisioni diverse per il progetto e il file di soluzione.

- I progetti sono stati aggiunti separatamente (in una soluzione controllata dal codice sorgente).

In è consigliabile che il nome della cartella SUR sia uguale al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nome della soluzione senza l'estensione . Nella tabella seguente viene riepilogato il comportamento nelle due versioni.

|Funzionalità|API del plug-in del controllo del codice sorgente versione 1.1|API plug-in del controllo del codice sorgente versione 1.2|
|-------------| - | - |
|Aggiungere una soluzione a SCC|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccGetProjPath()<br /><br /> SccOpenProject()|SccInitialize()<br /><br /> SccGetProjPath()<br /><br /> SccCreateSubProject()<br /><br /> SccCreateSubProject()<br /><br /> SccOpenProject()|
|Aggiungere un progetto alla soluzione con controllo del codice sorgente|SccGetProjPath()<br /><br /> OpenProject()|SccGetParentProjectPath()<br /><br /> SccOpenProject()<br /><br />  **Nota:** Visual Studio presuppone che una soluzione sia un elemento figlio diretto di SUR.  |

## <a name="examples"></a>Esempio
 Nella tabella seguente sono elencati due esempi. In entrambi i casi, all'utente viene richiesto di specificare un percorso di destinazione per la soluzione nel controllo del codice sorgente fino a quando user_choice specificato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come destinazione.  Quando viene specificato user_choice, la soluzione e i due progetti vengono aggiunti senza richiedere all'utente le destinazioni del controllo del codice sorgente.

|La soluzione contiene|Nei percorsi del disco|Struttura predefinita del database|
|-----------------------|-----------------------|--------------------------------|
|*sln1.sln*<br /><br /> Web1<br /><br /> Web2|*C:\Solutions\sln1*<br /><br /> *C:\Inetpub\wwwroot\Web1*<br /><br /> \\\server\wwwroot$\Web2|$/<user_choice>/sln1<br /><br /> $/<user_choice>/C/Web1<br /><br /> $/<user_choice>/Web2|
|*sln1.sln*<br /><br /> Web1<br /><br /> Win1|*C:\Solutions\sln1*<br /><br /> *D:\Inetpub\wwwroot\Web1*<br /><br /> *C:\solutions\sln1\Win1*|$/<user_choice>/sln1<br /><br /> $/<user_choice>/D/web1<br /><br /> $/<user_choice>/sln1/win1|

 La cartella SUR e le sottocartelle vengono create indipendentemente dal fatto che l'operazione sia annullata o non riesca a causa di un errore. Non vengono rimossi automaticamente nelle condizioni di annullamento o di errore.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'impostazione predefinita è il comportamento della versione 1.1 se il plug-in del controllo del codice sorgente non restituisce i flag `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` di funzionalità e . Inoltre, gli utenti di possono scegliere di ripristinare il comportamento della versione 1.1 impostando il valore della chiave seguente su [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *dword:00000001*:

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] DoNotCreateSolutionRootFolderInSourceControl**  =  *dword:00000001*

## <a name="see-also"></a>Vedi anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
