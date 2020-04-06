---
title: Funzione SccDiff . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701030"
---
# <a name="sccdiff-function"></a>SccDiff (funzione SccDiff)
Questa funzione visualizza (o facoltativamente controlla solo) le differenze tra il file corrente (sul disco locale) e l'ultima versione archiviata nel sistema di controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parametri
 pvContext

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 LpNomeFile

[in] Nome del file per il quale viene richiesta la differenza.

 fOpzioni

[in] Flag di comando. Per ulteriori informazioni, vedere Note.

 PvOpzioni

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La copia di lavoro e la versione del server sono identiche.|
|SCC_I_FILESDIFFERS|La copia di lavoro è diversa dalla versione nel controllo del codice sorgente.|
|SCC_I_RELOADFILE|Un file o un progetto deve essere ricaricato.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; differenza di file non è stata ottenuta.|
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|

## <a name="remarks"></a>Osservazioni
 Questa funzione ha due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco di modifiche apportate a un file. Il plug-in del controllo del codice sorgente apre la propria finestra, in qualsiasi formato si sceglie, per visualizzare le differenze tra il file dell'utente su disco e la versione più recente del file nel controllo del codice sorgente.

 In alternativa, l'IDE potrebbe semplicemente necessario determinare se un file è stato modificato. Ad esempio, l'IDE potrebbe essere necessario determinare se è sicuro per estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag. Il plug-in del controllo del codice sorgente deve controllare il file su disco, byte per byte, rispetto al file controllato dal codice sorgente e restituire un valore che indica se i due file sono diversi senza visualizzare nulla all'utente.

 Come ottimizzazione delle prestazioni, il plug-in del controllo del codice sorgente può utilizzare un'alternativa basata su un checksum o un timestamp anziché il confronto byte per byte richiesto da `SCC_DIFF_CONTENTS`: queste forme di confronto sono ovviamente più veloci ma meno affidabili. Non tutti i sistemi di controllo del codice sorgente possono supportare questi metodi di confronto alternativi e il plug-in potrebbe essere necessario eseguire il rollback a un confronto dei contenuti. Tutti i plug-in del controllo del codice sorgente devono, come minimo, supportare un confronto dei contenuti.

> [!NOTE]
> I flag di differenza rapida si escludono a vicenda. È valido non passare alcun flag, ma non è valido passare contemporaneamente più di uno. `SCC_DIFF_QUICK_DIFF`, che è una maschera che combina tutti i flag, può essere utilizzata per il test, ma non deve mai essere passata come parametro.

|`fOption`|Significato|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Confronto senza distinzione tra maiuscole e minuscole (può essere utilizzato per la differenza rapida o visiva).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere utilizzato per la differenza rapida o visiva).|
|SCC_DIFF_QD_CONTENTS|Confronta in modo invisibile all'utente il file, byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Confronta automaticamente il file tramite un checksum quando è supportato. Se non è supportato, esegue il fallback a un confronto dei contenuti.|
|SCC_DIFF_QD_TIME|Confronta il file in modo invisibile all'utente tramite il timestamp quando è supportato. Se non è supportato, esegue il fallback a un confronto dei contenuti.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
