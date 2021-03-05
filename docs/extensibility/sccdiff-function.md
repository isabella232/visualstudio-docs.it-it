---
description: Questa funzione Visualizza (o, facoltativamente, semplicemente controlla) le differenze tra il file corrente (sul disco locale) e l'ultima versione archiviato nel sistema di controllo del codice sorgente.
title: Funzione SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7f7573cafd8ea06537a7655897f3cc5907448cfa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220846"
---
# <a name="sccdiff-function"></a>SccDiff (funzione)
Questa funzione Visualizza (o, facoltativamente, semplicemente controlla) le differenze tra il file corrente (sul disco locale) e l'ultima versione archiviato nel sistema di controllo del codice sorgente.

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

in Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 lpFileName

in Nome file per il quale viene richiesta la differenza.

 fOptions

in Flag di comando. Per ulteriori informazioni, vedere Note.

 pvOptions

in Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La copia di lavoro e la versione del server sono identiche.|
|SCC_I_FILESDIFFERS|La copia di lavoro è diversa dalla versione del controllo del codice sorgente.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di conflitto. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. non è stata ottenuta la differenza del file.|
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|

## <a name="remarks"></a>Commenti
 Questa funzione serve due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco delle modifiche apportate a un file. Il plug-in del controllo del codice sorgente apre la propria finestra, in qualsiasi formato scelto, per visualizzare le differenze tra il file dell'utente su disco e la versione più recente del file nel controllo del codice sorgente.

 In alternativa, è possibile che l'IDE debba semplicemente determinare se un file è stato modificato. Ad esempio, è possibile che l'IDE debba determinare se è sicuro estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag. Il plug-in del controllo del codice sorgente deve controllare il file su disco, byte per byte, rispetto al file incluso nel controllo del codice sorgente e restituire un valore che indica se i due file sono diversi senza visualizzare alcun elemento all'utente.

 Per ottimizzare le prestazioni, il plug-in del controllo del codice sorgente può utilizzare un'alternativa basata su un checksum o un timestamp anziché il confronto byte per byte chiamato da `SCC_DIFF_CONTENTS` : queste forme di confronto sono ovviamente più veloci ma meno affidabili. Non tutti i sistemi di controllo del codice sorgente possono supportare questi metodi di confronto alternativi e il plug-in potrebbe dover eseguire il fallback a un confronto dei contenuti. Tutti i plug-in del controllo del codice sorgente devono supportare almeno un confronto di contenuti.

> [!NOTE]
> I flag di differenza rapida si escludono a vicenda. È possibile passare senza flag, ma non è possibile passare simultaneamente più di uno. `SCC_DIFF_QUICK_DIFF`, ovvero una maschera che combina tutti i flag, può essere usata per eseguire il test, ma non deve mai essere passata come parametro.

|`fOption`|Significato|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Confronto senza distinzione tra maiuscole e minuscole (può essere usato per una differenza rapida o visiva).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere utilizzato per una differenza rapida o visiva).|
|SCC_DIFF_QD_CONTENTS|Confronta automaticamente il file, byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Confronta automaticamente il file tramite un checksum, se supportato. Se non è supportato, viene eseguito il fallback a un confronto di contenuto.|
|SCC_DIFF_QD_TIME|Confronta automaticamente il file con il timestamp quando è supportato. Se non è supportato, viene eseguito il fallback a un confronto di contenuto.|

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
