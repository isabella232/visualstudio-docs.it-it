---
title: Funzioni API plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni sulle funzioni fornite dall'API plug-in del controllo del codice sorgente, che devono essere implementate dal plug-in del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f93ddff78aa151218d0b46d017e4631d9489e44
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899602"
---
# <a name="source-control-plug-in-api-functions"></a>Funzioni API del plug-in del controllo del codice sorgente
L'API plug-in del controllo del codice sorgente fornisce le funzioni seguenti, che devono essere implementate dal plug-in di controllo del codice sorgente in base a questa API. Le firme di ogni funzione e la semantica associata ai flag di bit e ad altri parametri sono descritte in dettaglio in questo riferimento.

## <a name="initialization-and-housekeeping-functions"></a>Funzioni di inizializzazione e gestione delle pulizie

|Funzione|Descrizione|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Chiude un progetto.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Richiede all'utente le opzioni avanzate per il comando specificato.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Restituisce la versione del plug-in del controllo del codice sorgente.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inizializza il plug-in del controllo del codice sorgente. Viene chiamato una volta per ogni istanza del plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Apre un progetto.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Funzione generica usata per impostare un'ampia gamma di opzioni. Ogni opzione inizia con `SCC_OPT_xxx` e ha un proprio set definito di valori.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Chiamato una volta quando un plug-in del controllo del codice sorgente deve essere scollegato.|

## <a name="core-source-control-functions"></a>Funzioni di base del controllo del codice sorgente

|Funzione|Descrizione|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Aggiunge una matrice di file specificati dai nomi di percorso completi al sistema di controllo del codice sorgente.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Consente all'utente di cercare i file già presenti nel sistema di controllo del codice sorgente e quindi di rendere tali file parte del progetto corrente.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Controlla una matrice di file.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Esegue il check-out di una matrice di file.|
|[SccDiff](../extensibility/sccdiff-function.md)|Mostra le differenze tra il file dell'utente locale specificato da un nome di percorso completo e la versione nel controllo del codice sorgente.|
|[SccGet](../extensibility/sccget-function.md)|Recupera una copia di sola lettura di un set di file.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Controlla lo stato dei file che il chiamante ha richiesto (tramite `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Fa in modo che il plug-in del controllo del codice sorgente inseri la richiesta all'utente di un percorso di progetto significativo per il plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Visualizza la cronologia per una matrice di nomi di file locali completi.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Esamina l'elenco dei file per il relativo stato corrente. Usa inoltre la funzione per inviare una notifica al chiamante quando un file non corrisponde `pfnPopulate` ai criteri per `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Mostra le proprietà di un file completo.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Esamina un elenco di file completi per il relativo stato corrente.|
|[SccRemove](../extensibility/sccremove-function.md)|Rimuove la matrice di file completi dal sistema di controllo del codice sorgente.|
|[SccRename](../extensibility/sccrename-function.md)|Rinomina il file specificato con un nuovo nome nel sistema di controllo del codice sorgente.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Accede all'intera gamma di funzionalità del sistema di controllo del codice sorgente.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Annulla un'estrazione di una matrice di file.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità aggiuntive (versione 1.2 dell'API plug-in del controllo del codice sorgente)
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.2 dell'API plug-in del controllo del codice sorgente. Forniscono l'accesso a funzionalità e funzionalità di controllo del codice sorgente più avanzate.

|Funzione|Descrizione|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Avvia un'operazione batch.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Crea un sottoprogetto con il nome specificato in un progetto padre esistente.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Mostra le differenze tra la directory dell'utente locale specificata da un nome di percorso completo e il percorso del database del controllo del codice sorgente.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Esamina un elenco di directory completo per il relativo stato corrente.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Termina un'operazione batch.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Restituisce il percorso padre del progetto specificato (il progetto deve esistere).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Verifica se sono consentite più estrazioni in un file.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Verifica se il plug-in creerà MSSCCPRJ. File SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funzioni che supportano funzionalità avanzate (versione 1.3 dell'API plug-in del controllo del codice sorgente)
 Questo gruppo di funzioni definisce le funzionalità aggiuntive incluse nella versione 1.3 dell'API plug-in del controllo del codice sorgente. Forniscono l'accesso a funzionalità e funzionalità di controllo del codice sorgente più avanzate.

|Funzione|Descrizione|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file dal controllo del codice sorgente al progetto corrente.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Recupera un elenco di file dal controllo del codice sorgente senza un'interfaccia utente.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Recupera un elenco di file nel controllo del codice sorgente diversi dai file locali.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Recupera i flag che specificano le funzionalità estese supportate dal plug-in del controllo del codice sorgente.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Recupera le opzioni specifiche dell'utente.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Esamina un elenco di directory e file in uno o più progetti sotto controllo del codice sorgente. Ogni directory e nome file trovato viene passato a una funzione di callback.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Esamina le modifiche dei nomi apportate a un elenco di file. Ogni nome file viene passato a una funzione di callback con il relativo stato di modifica.|

## <a name="requirements"></a>Requisiti
 Intestazione: scc.h

 (Inclusa nella cartella Include comune dell'SDK dell'ambiente, per impostazione predefinita *[unità]* \Programmi\VSIP 8.0\EnvSDK\common\inc; fornita anche nella cartella VSIP con l'esempio MSSCCI, *[unità]* \Programmi\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)
