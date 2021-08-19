---
title: Flag di bit usati da comandi specifici | Microsoft Docs
description: Informazioni sui flag di bit usati dall'API plug-in del controllo del codice sorgente, organizzati in base alla funzione che li usa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9cfa48cc8ef55e8fcd574055d1d0c6acc9c84935
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043830"
---
# <a name="bitflags-used-by-specific-commands"></a>Flag di bit usati da comandi specifici
Il comportamento di una serie di funzioni nell'API plug-in del controllo del codice sorgente può essere modificato impostando uno o più bit in un singolo valore. Questi valori sono noti come flag di bit. I vari flag di bit usati dall'API plug-in del controllo del codice sorgente sono dettagliati qui, raggruppati in base alla funzione che li usa.

## <a name="checked-out-flag"></a>Flag estratto
 Questo flag può essere impostato per [SccAdd](../extensibility/sccadd-function.md) o [SccCheckin](../extensibility/scccheckin-function.md).

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenere il file estratto.|

## <a name="add-flags"></a>Aggiungere flag
 Questi flag vengono usati da [SccAdd](../extensibility/sccadd-function.md).

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|È previsto che il plug-in del controllo del codice sorgente rilevi automaticamente se il file è di tipo testo o binario.|
|`SCC_FILETYPE_TEXT`|0x01|Il tipo di file è text.|
|`SCC_FILETYPE_BINARY`|0x04|Il tipo di file è binario. **Nota:** `SCC_FILETYPE_TEXT` i `SCC_FILETYPE_BINARY` flag e si escludono a vicenda.   Impostare esattamente uno o nessuno dei due valori.|
|`SCC_ADD_STORELATEST`|0x02|Archiviare solo la versione più recente (nessun delta).|

## <a name="diff-flags"></a>Flag di diff
 [SccDiff usa](../extensibility/sccdiff-function.md) questi flag per definire l'ambito di un'operazione diff. I `SCC_DIFF_QD_xxx` flag si escludono a vicenda. Se ne viene specificato uno, non deve essere fornito alcun feedback visivo. In una "diff rapida" (QD), il plug-in non determina in che modo il file è diverso, solo se è diverso. Se non viene specificato nessuno di questi flag, viene eseguita una "diff visiva". vengono calcolate e visualizzate le differenze dettagliate dei file. Se il QD richiesto non è supportato, il plug-in passa a quello migliore successivo. Ad esempio, se l'IDE richiede un checksum e il plug-in non lo supporta, il plug-in esegue un controllo completo del contenuto (ancora molto più veloce di una visualizzazione visiva).

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorare le differenze tra maiuscole e minuscole.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorare le differenze tra spazi vuoti. **Nota:**  I `SCC_DIFF_IGNORECASE` flag e sono flag di bit `SCC_DIFF_IGNORESPACE` facoltativi.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD confrontando l'intero contenuto del file.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD in base al checksum.|
|`SCC_DIFF_QD_TIME`|0x0040|QD in base al timestamp di data/ora del file.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Si tratta di una maschera usata per controllare tutti i bitflag QD. Non deve essere passato in una funzione. i tre flag di bit QD si escludono a vicenda. QD indica sempre nessuna visualizzazione dell'interfaccia utente.|

## <a name="populatelist-flag"></a>Flag PopulateList
 Questo flag viene usato da [SccPopulateList](../extensibility/sccpopulatelist-function.md) nel `fOptions` parametro .

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|L'IDE passa le directory, non i file.|

## <a name="populatedirlist-flags"></a>Flag PopulateDirList
 Questi flag vengono usati da [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) nel `fOptions` parametro .

|Valore dell'opzione|Valore|Descrizione|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Esaminare solo un livello di directory per le directory (impostazione predefinita).|
|SCC_PDL_RECURSIVE|0x0001|Esaminare in modo ricorsivo tutte le directory in ogni directory specificata.|
|SCC_PDL_INCLUDEFILES|0x0002|Includere i nomi di file nel processo di esame.|

## <a name="openproject-flags"></a>Flag OpenProject
 Questi flag vengono usati da [SccOpenProject](../extensibility/sccopenproject-function.md) nel `dwFlags` parametro .

|Valore dell'opzione|Valore|Descrizione|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Se il progetto non esiste nel controllo del codice sorgente, crearlo. Se questo flag non è impostato, richiedere all'utente di creare il progetto (a meno che `SCC_OP_SILENTOPEN` non venga specificato il flag).|
|SCC_OP_SILENTOPEN|0x00000002L|Non richiedere all'utente di creare un progetto. restituisce solo `SCC_E_UNKNOWNPROJECT` .|

## <a name="get-flags"></a>Ottenere i flag
 Questi flag vengono usati da [SccGet](../extensibility/sccget-function.md) e [SccCheckout](../extensibility/scccheckout-function.md).

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|L'IDE passa le directory, non i file: ottiene tutti i file in queste directory.|
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE passa le directory: ottenere queste directory e tutte le relative sottodirectory.|

## <a name="noption-values"></a>Valori di nOption
 Questi flag vengono usati da [SccSetOption](../extensibility/sccsetoption-function.md) nel `nOption` parametro .

|Flag|valore|Descrizione|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Impostare lo stato della coda degli eventi.|
|`SCC_OPT_USERDATA`|0x00000002L|Specificare i dati utente per `SCC_OPT_NAMECHANGEPFN` .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE può gestire l'annullamento.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Impostare un callback per le modifiche dei nomi.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Disabilitare l'estrazione dell'interfaccia utente del plug-in del controllo del codice sorgente e non impostare la directory di lavoro.|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Aggiungere dal sistema di controllo del codice sorgente per specificare una directory di lavoro. Provare a condividere nel progetto associato se è un discendente diretto.|

## <a name="dwval-bitflags"></a>Flag di bit dwVal
 Questi flag vengono usati da [SccSetOption](../extensibility/sccsetoption-function.md) nel `dwVal` parametro .

|Flag|valore|Descrizione|Usato per `nOption` valore|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Sospende l'attività della coda di eventi.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Abilita la registrazione delle code di eventi.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Impostazione predefinita) Non ha la modalità di annullamento. Se lo si desidera, il plug-in deve fornire .|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|L'IDE gestisce l'annullamento.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Impostazione predefinita) OK per estrarre dall'interfaccia utente del plug-in. la directory di lavoro è impostata.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Nessuna estrazione dell'interfaccia utente del plug-in, nessuna directory di lavoro.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
