---
description: Questa funzione consente di visualizzare (o, facoltativamente, solo di verificare) le differenze tra il file corrente (sul disco locale) e l'ultima versione archiviata nel sistema di controllo del codice sorgente.
title: Funzione SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 484d8b5e988ede9b50099e3c0376f2c3afce8317
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904656"
---
# <a name="sccdiff-function"></a>Funzione SccDiff
Questa funzione consente di visualizzare (o, facoltativamente, solo di verificare) le differenze tra il file corrente (sul disco locale) e l'ultima versione archiviata nel sistema di controllo del codice sorgente.

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

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 hWnd

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 lpFileName

[in] Nome file per cui è richiesta la differenza.

 fOptions

[in] Flag di comando. Per ulteriori informazioni, vedere Note.

 pvOptions

[in] Opzioni specifiche del plug-in del controllo del codice sorgente.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La copia di lavoro e la versione del server sono identiche.|
|SCC_I_FILESDIFFERS|La copia di lavoro è diversa dalla versione nel controllo del codice sorgente.|
|SCC_I_RELOADFILE|È necessario ricaricare un file o un progetto.|
|SCC_E_FILENOTCONTROLLED|Il file non è sotto il controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile riprovare.|
|SCC_E_NONSPECIFICERROR|Errore non specifico; La differenza di file non è stata ottenuta.|
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|

## <a name="remarks"></a>Commenti
 Questa funzione ha due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco di modifiche apportate a un file. Il plug-in del controllo del codice sorgente apre una finestra separata, nel formato scelto, per visualizzare le differenze tra il file dell'utente su disco e la versione più recente del file nel controllo del codice sorgente.

 In alternativa, l'IDE potrebbe semplicemente dover determinare se un file è stato modificato. Ad esempio, l'IDE potrebbe dover determinare se è sicuro estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag . Il plug-in del controllo del codice sorgente deve controllare il file su disco, byte per byte, rispetto al file controllato dal codice sorgente e restituire un valore che indica se i due file sono diversi senza visualizzare nulla all'utente.

 Come ottimizzazione delle prestazioni, il plug-in del controllo del codice sorgente può usare un'alternativa basata su un checksum o un timestamp anziché il confronto byte per byte chiamato da : queste forme di confronto sono ovviamente più veloci ma meno `SCC_DIFF_CONTENTS` affidabili. Non tutti i sistemi di controllo del codice sorgente possono supportare questi metodi di confronto alternativi e il plug-in potrebbe essere necessario eseguire il fall back a un confronto del contenuto. Tutti i plug-in del controllo del codice sorgente devono supportare almeno un confronto dei contenuti.

> [!NOTE]
> I flag di differenza rapida si escludono a vicenda. Non è possibile passare alcun flag, ma non è valido passare contemporaneamente più flag. `SCC_DIFF_QUICK_DIFF`, che è una maschera che combina tutti i flag, può essere usata per il test, ma non deve mai essere passata come parametro.

|`fOption`|Significato|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Confronto senza distinzione tra maiuscole e minuscole (può essere usato per differenze rapide o visive).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere usato per differenze rapide o visive).|
|SCC_DIFF_QD_CONTENTS|Confronta automaticamente il file, byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Confronta automaticamente il file tramite un checksum, se supportato. Se non è supportato, viene eseguito il falls back a un confronto del contenuto.|
|SCC_DIFF_QD_TIME|Confronta automaticamente il file tramite il relativo timestamp, se supportato. Se non è supportato, viene eseguito il falls back a un confronto del contenuto.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
