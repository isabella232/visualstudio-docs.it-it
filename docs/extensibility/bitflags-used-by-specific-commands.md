---
title: Flag utilizzato da comandi specifici | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740006"
---
# <a name="bitflags-used-by-specific-commands"></a>Flag utilizzato da comandi specifici
Il comportamento di un numero di funzioni nell'API del plug-in del controllo del codice sorgente può essere modificato impostando uno o più bit in un singolo valore. Questi valori sono noti come flag. Le varie flag utilizzate dall'API del plug-in del controllo del codice sorgente sono descritte in questo argomento, raggruppate in base alla funzione che le utilizza.

## <a name="checked-out-flag"></a>Flag Estratto
 Questo flag può essere impostato sia per [SccAdd](../extensibility/sccadd-function.md) che per [SccCheckin](../extensibility/scccheckin-function.md).

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Lasciare il file estratto.|

## <a name="add-flags"></a>Aggiungi flag
 Questi flag vengono usati da [SccAdd](../extensibility/sccadd-function.md).

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|È previsto che il plug-in del controllo del codice sorgente rilevi automaticamente se il file è di tipo text o Binary.|
|`SCC_FILETYPE_TEXT`|0x01|Il tipo di file è testo.|
|`SCC_FILETYPE_BINARY`|0x04|Il tipo di file è binario. **Nota:** `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` flag e si escludono a vicenda.   Impostare esattamente uno o nessuno.|
|`SCC_ADD_STORELATEST`|0x02|Archivia solo la versione più recente (nessun Delta).|

## <a name="diff-flags"></a>Flag diff
 [SccDiff](../extensibility/sccdiff-function.md) utilizza questi flag per definire l'ambito di un'operazione diff. I `SCC_DIFF_QD_xxx` flag si escludono a vicenda. Se viene specificato uno di essi, non verrà fornito alcun feedback visivo. In una "diff rapido" (QD), il plug-in non determina come il file è diverso, solo se è diverso. Se non viene specificato alcun flag, viene eseguita una "diff visiva"; le differenze di file dettagliate vengono calcolate e visualizzate. Se la richiesta non è supportata, il plug-in passa a quello più prossimo. Se, ad esempio, l'IDE richiede un checksum e il plug-in non lo supporta, il plug-in esegue un controllo del contenuto completo (ancora molto più veloce rispetto a una visualizzazione visiva).

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignora differenze tra maiuscole e minuscole.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignora le differenze di spazio vuoto. **Nota:**  I `SCC_DIFF_IGNORECASE` flag `SCC_DIFF_IGNORESPACE` e sono facoltativi flag.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD confrontando tutto il contenuto del file.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD per checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|QD per data/ora del file.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Si tratta di una maschera utilizzata per controllare tutti i flag QD. Non deve essere passato in una funzione; i tre flag QD si escludono a vicenda. QD non indica sempre alcuna visualizzazione dell'interfaccia utente.|

## <a name="populatelist-flag"></a>Flag popolamento
 Questo flag viene usato da [SccPopulateList](../extensibility/sccpopulatelist-function.md) nel `fOptions` parametro.

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|L'IDE passa le directory, non i file.|

## <a name="populatedirlist-flags"></a>Flag PopulateDirList
 Questi flag vengono usati da [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) nel `fOptions` parametro.

|Valore dell'opzione|Valore|Descrizione|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Esaminare solo un livello di directory per le directory (impostazione predefinita).|
|SCC_PDL_RECURSIVE|0x0001|Esaminare in modo ricorsivo tutte le directory in ogni directory specificata.|
|SCC_PDL_INCLUDEFILES|0x0002|Includere i nomi di file nel processo di analisi.|

## <a name="openproject-flags"></a>Flag OpenProject
 Questi flag vengono usati da [SccOpenProject](../extensibility/sccopenproject-function.md) nel `dwFlags` parametro.

|Valore dell'opzione|Valore|Descrizione|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Se il progetto non esiste nel controllo del codice sorgente, crearlo. Se questo flag non è impostato, richiedere all'utente il progetto di creare (a `SCC_OP_SILENTOPEN` meno che non sia specificato il flag).|
|SCC_OP_SILENTOPEN|0x00000002L|Non richiedere all'utente di creare un progetto; Basta restituire `SCC_E_UNKNOWNPROJECT`.|

## <a name="get-flags"></a>Ottenere i flag
 Questi flag vengono usati da [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|L'IDE passa le directory e non i file: recuperare tutti i file in queste directory.|
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE passa le directory: ottenere queste directory e tutte le relative sottodirectory.|

## <a name="noption-values"></a>valori nOption
 Questi flag vengono usati da [SccSetOption](../extensibility/sccsetoption-function.md) nel `nOption` parametro.

|Flag|Valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Impostare lo stato della coda degli eventi.|
|`SCC_OPT_USERDATA`|0x00000002L|Specificare i dati utente `SCC_OPT_NAMECHANGEPFN`per.|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE può gestire l'annullamento.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Imposta un callback per le modifiche del nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Disabilitare l'estrazione dell'interfaccia utente del plug-in del controllo del codice sorgente e non impostare la directory di lavoro.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Aggiungere dal sistema di controllo del codice sorgente per specificare una directory di lavoro. Provare a condividere nel progetto associato se è un discendente diretto.|

## <a name="dwval-bitflags"></a>flag dwVal
 Questi flag vengono usati da [SccSetOption](../extensibility/sccsetoption-function.md) nel `dwVal` parametro.

|Flag|Valore|Descrizione|Usato per `nOption` valore|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Sospende l'attività della coda di eventi.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Abilita la registrazione della coda degli eventi.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|Predefinita Non ha modalità di annullamento; Se lo si desidera, è necessario specificare il plug-in.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|Handle dell'IDE Annulla.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|Predefinita OK per estrarre dall'interfaccia utente del plug-in. la directory di lavoro è impostata.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Nessun checkout dell'interfaccia utente plug-in, nessuna directory di lavoro.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
