---
title: Flag di bit usati da comandi specifici | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43dc083812bc172fe4a9f80335742b3faab2e1f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967053"
---
# <a name="bitflags-used-by-specific-commands"></a>Flag di bit usati da comandi specifici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il comportamento di un numero di funzioni nell'API dei plug-in controllo di origine può essere modificato impostando uno o più bit in un singolo valore. Questi valori sono noti come flag di bit. I vari flag di bit usati dall'API dei plug-in controllo di origine sono descritte in dettaglio in questo caso, raggruppati per la funzione che li Usa.  
  
## <a name="checked-out-flag"></a>Flag di stato estratto  
 Questo flag può essere impostato per entrambi i [SccAdd](../extensibility/sccadd-function.md) oppure [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenere il file estratto.|  
  
## <a name="add-flags"></a>Aggiungi flag  
 Questi flag vengono utilizzati per il [SccAdd](../extensibility/sccadd-function.md).  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|È previsto il plug-in del controllo del codice sorgente per rilevare automaticamente se il file è di tipo testo o binario.|  
|`SCC_FILETYPE_TEXT`|0x01|Tipo di file è testo.|  
|`SCC_FILETYPE_BINARY`|0x04|Tipo di file è binario. **Nota:** `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` flag si escludono a vicenda. Impostare uno o nessuno.|  
|`SCC_ADD_STORELATEST`|0x02|Store solo l'ultima versione (non i delta).|  
  
## <a name="diff-flags"></a>Flag diff  
 Il [SccDiff](../extensibility/sccdiff-function.md) utilizza questi flag per definire l'ambito di un'operazione diff. Il `SCC_DIFF_QD_xxx` flag si escludono a vicenda. Se viene specificato uno di essi, quindi alcun feedback visivo non è necessario fornire. In un "diff veloce" (PC), il plug-in non determina come il file è diverso, solo se è diverso. Se nessuno di questi flag sono specificati, che viene eseguito un "diff visual"; le differenze tra file dettagliato vengono calcolate e visualizzate. Se il PC richiesto non è supportato, il plug-in passa al successivo quello più adatto. Ad esempio, se l'IDE richiede un checksum e il plug-in non è supportata, l'oggetto non del plug-in un full-contenuto, selezionare (comunque molto più velocemente una rappresentazione visiva).  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignora le maiuscole.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorare le differenze di spazio vuoto. **Nota:**  Il `SCC_DIFF_IGNORECASE` e `SCC_DIFF_IGNORESPACE` flag sono facoltativi flag di bit.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|PC confrontando l'intero contenuto del file.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|PC da checksum.|  
|`SCC_DIFF_QD_TIME`|0x0040|Profondità coda per un timbro data/ora di file.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Si tratta di una maschera utilizzata per controllare tutti i flag di bit PC. Non deve essere passato in una funzione; i tre flag di bit di PC si escludono a vicenda. PC non significa sempre visualizzare alcuna interfaccia utente.|  
  
## <a name="populatelist-flag"></a>Flag PopulateList  
 Questo flag viene utilizzato per il [SccPopulateList](../extensibility/sccpopulatelist-function.md) nel `fOptions` parametro.  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|L'IDE passa le directory, non i file.|  
  
## <a name="populatedirlist-flags"></a>Flag PopulateDirList  
 Questi flag vengono utilizzati per il [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) nel `fOptions` parametro.  
  
|Valore dell'opzione|Value|Descrizione|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Esaminare un solo livello di directory per le directory (questo è il valore predefinito).|  
|SCC_PDL_RECURSIVE|0x0001|In modo ricorsivo, esaminare tutte le directory in ogni directory specificata.|  
|SCC_PDL_INCLUDEFILES|0x0002|Includere i nomi di file nel processo di esame.|  
  
## <a name="openproject-flags"></a>Flag OpenProject  
 Questi flag vengono utilizzati per il [SccOpenProject](../extensibility/sccopenproject-function.md) nel `dwFlags` parametro.  
  
|Valore dell'opzione|Value|Descrizione|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Se il progetto non esiste nel controllo del codice sorgente, è necessario crearla. Se questo flag non è impostato, richiesta utente per il progetto da creare (a meno che non `SCC_OP_SILENTOPEN` flag è specificato).|  
|SCC_OP_SILENTOPEN|0x00000002L|Non chiedere conferma all'utente di creare un progetto. semplicemente restituire `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Ottenere i flag  
 Questi flag vengono utilizzati per il [SccGet](../extensibility/sccget-function.md) e il [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|L'IDE passa le directory, non file: Ottenere tutti i file in tali directory.|  
|`SCC_GET_RECURSIVE`|0x00000002L|L'IDE passa le directory: Ottenere queste directory e tutte le sottodirectory.|  
  
## <a name="noption-values"></a>Valori nOption  
 Questi flag vengono utilizzati per il [SccSetOption](../extensibility/sccsetoption-function.md) nel `nOption` parametro.  
  
|Flag|Value|Descrizione|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Impostare lo stato della coda di eventi.|  
|`SCC_OPT_USERDATA`|0x00000002L|Specificare i dati utente per `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|L'IDE può gestire Annulla|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Impostare un callback per modifiche ai nomi.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Disabilitare l'estrazione dell'interfaccia utente del plug-in del controllo sorgente e non si imposta la directory di lavoro.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Aggiungere dal sistema di controllo di origine per specificare una directory di lavoro. Provare a condividere nel progetto associato se è un discendente diretto.|  
  
## <a name="dwval-bitflags"></a>dwVal i flag di bit  
 Questi flag vengono utilizzati per il [SccSetOption](../extensibility/sccsetoption-function.md) nel `dwVal` parametro.  
  
|Flag|Value|Descrizione|Usato da `nOption` valore|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Sospende l'attività dell'evento della coda.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Abilita la registrazione della coda eventi.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Impostazione predefinita) Non possiede alcuna modalità di annullamento; plug-in è necessario specificare se lo si desidera.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|L 1|IDE gestisce l'annullamento.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Impostazione predefinita) OK per estrarre dal plug-in dell'interfaccia utente; directory di lavoro è impostata.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|L 1|Nessun Checkpoint dell'interfaccia utente del plug-in, alcuna directory di lavoro.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
