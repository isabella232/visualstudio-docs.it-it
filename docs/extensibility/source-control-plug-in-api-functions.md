---
title: Funzioni API del plug-in controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d73dd67f0f2d64a2ac02c77b2eb86d21e559c0d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880036"
---
# <a name="source-control-plug-in-api-functions"></a>Funzioni API del plug-in del controllo del codice sorgente
L'API dei plug-in del controllo origine fornisce le funzioni seguenti, che devono essere implementate dal controllo del codice sorgente del plug-in conformità con questa API. Le firme di ogni funzione e la semantica associata con il flag di bit e altri parametri sono descritti in dettaglio in questo riferimento.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inizializzazione e funzioni di manutenzione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Chiude un progetto.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Richiede all'utente le opzioni avanzate per il comando specificato.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Restituisce la versione del controllo del codice sorgente del plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inizializza il plug-in del controllo del codice sorgente. Viene chiamato una volta per ogni istanza del plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Apre un progetto.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Una funzione generica consente di impostare un'ampia gamma di opzioni. Ogni opzione di avvio con `SCC_OPT_xxx` e ha un proprio set definito di valori.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chiamato una volta quando un plug-in del controllo del codice sorgente deve essere scollegato.|  
  
## <a name="core-source-control-functions"></a>Funzioni di controllo di base origine  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Aggiunge una matrice di file specificato da nomi di percorso completo al sistema di controllo di origine.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Consente di individuare i file già presenti nel sistema di controllo di origine e quindi rendere tali file che fanno parte del progetto corrente.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Controlli in una matrice di file.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Consente di estrarre una matrice di file.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Illustra le differenze tra file dell'utente locale specificato da un nome percorso completo e la versione controllo del codice sorgente.|  
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia di sola lettura di un set di file.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Controlla lo stato del file che il chiamante ha richiesto sulla (tramite `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Fa sì che il plug-in per richiedere all'utente per un percorso di progetto che è significativo per il plug-in del controllo del codice sorgente.|  
|[SccHistory](../extensibility/scchistory-function.md)|Mostra la cronologia per una matrice dei nomi completo del file locale.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Esamina l'elenco dei file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Mostra le proprietà di un file completo.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Esamina un elenco di file completi per il relativo stato corrente.|  
|[SccRemove](../extensibility/sccremove-function.md)|Rimuove la matrice di file completi dal sistema di controllo di origine.|  
|[SccRename](../extensibility/sccrename-function.md)|Rinomina il file specificato in un nuovo nome nel sistema di controllo di origine.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accede l'intera gamma di funzionalità del sistema di origine.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annulla l'estrazione di una matrice di file.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funzioni che supportano la funzionalità aggiuntiva (versione 1.2 dell'API del plug-in del controllo di origine)  
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.2 dell'API dei plug-in controllo di origine. Forniscono l'accesso a funzionalità di controllo del codice sorgente e le funzionalità più avanzate.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Avvia un'operazione batch.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un sottoprogetto con il nome specificato in un progetto padre esistente.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Illustra le differenze tra directory dell'utente locale specificato da un nome percorso completo e il percorso di database di controllo di origine.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Esamina un elenco di directory completo per il relativo stato corrente.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina un'operazione batch.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Restituisce padre percorso del progetto specificato (il progetto deve essere presente).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Controlla se sono consentite le estrazioni multiple in un file.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Controlla se il plug-in creerà MSSCCPRJ. File SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità avanzate (versione 1.3 dell'API del plug-in del controllo di origine)  
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.3 dell'API dei plug-in controllo di origine. Forniscono l'accesso a funzionalità di controllo del codice sorgente e le funzionalità più avanzate.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file dal controllo del codice sorgente al progetto corrente.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera un elenco di file dal controllo del codice sorgente senza un'interfaccia utente.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera un elenco di file nel controllo del codice sorgente che sono diversi dai file locali.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera i flag che specificano le funzionalità estese supportate dal plug-in del controllo del codice sorgente.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera le opzioni specifiche dell'utente.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Esamina un elenco di directory e file in un progetto o i progetti sottoposti al controllo del codice sorgente. Ogni nome di directory e file trovato viene passato a una funzione di callback.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Esamina modifiche di nome apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback con lo stato di modifica.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: scc.h  
  
 (Fornita nel SDK di ambiente comuni include cartelle, per impostazione predefinita *[unità]* 8.0\EnvSDK\common\inc \Program Files\VSIP; specificata anche nella cartella con il codice di esempio MSSCCI, VSIP *[unità]* \Programmi Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)