---
title: Funzioni dell'API del plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699915"
---
# <a name="source-control-plug-in-api-functions"></a>Funzioni API del plug-in del controllo del codice sorgente
L'API del plug-in del controllo del codice sorgente fornisce le funzioni seguenti, che devono essere implementate dal plug-in del controllo del codice sorgente in conformità con questa API. Le firme di ogni funzione e la semantica associata ai flag di bit e ad altri parametri sono descritte in dettaglio in questo riferimento.

## <a name="initialization-and-housekeeping-functions"></a>Funzioni di inizializzazione e pulizia

|Funzione|Descrizione|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Chiude un progetto.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Richiede all'utente le opzioni avanzate per il comando specificato.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Restituisce la versione del plug-in del controllo del codice sorgente.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inizializza il plug-in del controllo del codice sorgente. Viene chiamato una volta per ogni istanza del plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Apre un progetto.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funzione generica utilizzata per impostare un'ampia gamma di opzioni. Ogni opzione `SCC_OPT_xxx` inizia con e ha un proprio set definito di valori.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chiamato una volta quando un plug-in del controllo del codice sorgente deve essere scollegato.|

## <a name="core-source-control-functions"></a>Funzioni di controllo del codice sorgente di baseCore Source Control Functions

|Funzione|Descrizione|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Aggiunge una matrice di file specificati da nomi di percorso completi al sistema di controllo del codice sorgente.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e quindi rendere tali file parte del progetto corrente.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Archivia una serie di file.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Controlla una serie di file.|
|[SccDiff](../extensibility/sccdiff-function.md)|Mostra le differenze tra il file dell'utente locale specificato da un nome di percorso completo e la versione nel controllo del codice sorgente.|
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia di sola lettura di un set di file.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Controlla lo stato dei file che il `SccQueryInfo`chiamante ha chiesto (tramite ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Fa in modo che il plug-in del controllo del codice sorgente richieda all'utente un percorso di progetto significativo per il plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Visualizza la cronologia di una matrice di nomi di file locali completi.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Esamina l'elenco dei file per il relativo stato corrente. Viene inoltre utilizzata `pfnPopulate` la funzione per notificare al chiamante `nCommand`quando un file non corrisponde ai criteri per il file .|
|[SccProperties](../extensibility/sccproperties-function.md)|Mostra le proprietà di un file completo.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Esamina un elenco di file completi per il relativo stato corrente.|
|[SccRemove](../extensibility/sccremove-function.md)|Rimuove la matrice di file completi dal sistema di controllo del codice sorgente.|
|[SccRename](../extensibility/sccrename-function.md)|Rinomina il file specificato con un nuovo nome nel sistema di controllo del codice sorgente.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accede all'intera gamma di funzionalità del sistema di controllo del codice sorgente.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annulla un'estrazione di una serie di file.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità aggiuntive (versione 1.2 dell'API del plug-in del controllo del codice sorgente)
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.2 dell'API del plug-in del controllo del codice sorgente. Forniscono l'accesso a funzionalità e funzionalità di controllo del codice sorgente più avanzate.

|Funzione|Descrizione|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Avvia un'operazione batch.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un sottoprogetto con il nome specificato in un progetto padre esistente.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Mostra le differenze tra la directory dell'utente locale specificata da un nome di percorso completo e il percorso del database del controllo del codice sorgente.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Esamina un elenco di directory complete per il relativo stato corrente.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina un'operazione batch.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Restituisce il percorso padre del progetto specificato (il progetto deve esistere).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Controlla se sono consentite più estrazioni di un file.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Controlla se il plug-in creerà MSSCCPRJ. file SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità avanzate (versione 1.3 dell'API del plug-in del controllo del codice sorgente)
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.3 dell'API del plug-in del controllo del codice sorgente. Forniscono l'accesso a funzionalità e funzionalità di controllo del codice sorgente più avanzate.

|Funzione|Descrizione|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file dal controllo del codice sorgente al progetto corrente.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera un elenco di file dal controllo del codice sorgente senza un'interfaccia utente.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera un elenco di file nel controllo del codice sorgente diversi dai file locali.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera i flag che specificano le funzionalità estese supportate dal plug-in del controllo del codice sorgente.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera le opzioni specifiche dell'utente.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Esamina un elenco di directory e file in un progetto o progetti che si trovano nel controllo del codice sorgente. Ogni directory e nome file trovato viene passato a una funzione di callback.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Esamina le modifiche al nome apportate a un elenco di file. Ogni nome di file viene passato a una funzione di callback con il relativo stato di modifica.|

## <a name="requirements"></a>Requisiti
 Intestazione: scc.h

 (Fornito nella cartella comune di Environment SDK include, per impostazione predefinita *[unità] .* *[drive]*

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)
