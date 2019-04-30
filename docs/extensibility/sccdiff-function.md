---
title: Funzione SccDiff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed96b7c893ba3ececb33be5dda55093b70c28659
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434688"
---
# <a name="sccdiff-function"></a>Funzione SccDiff
Questa funzione consente di visualizzare (o facoltativamente appena Cerca) le differenze tra il file corrente (nel disco locale) e la relativa versione ultimo stato archiviato nell'origine del sistema di controllo.

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

[in] La struttura del contesto plug-in del controllo origine.

 hWnd

[in] Handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente è possibile utilizzare come padre per le finestre di dialogo che fornisce.

 lpFileName

[in] Nome del file per il quale viene richiesta la differenza.

 fOptions

[in] Flag di comando. Per informazioni dettagliate, vedere la sezione Osservazioni.

 pvOptions

[in] Opzioni specifiche plug-in controllo sorgente.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|La versione di copia e il server di lavoro sono identici.|
|SCC_I_FILESDIFFERS|La copia di lavoro è diverso dalla versione di controllo del codice sorgente.|
|SCC_I_RELOADFILE|Un progetto o il file deve essere ricaricato.|
|SCC_E_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR|Errore non specifico. differenza tra i file non è stato ottenuto.|
|SCC_E_FILENOTEXIST|Il file locale non è stato trovato.|

## <a name="remarks"></a>Note
 Questa funzione ha due scopi diversi. Per impostazione predefinita, viene visualizzato un elenco delle modifiche in un file. Il plug-in del controllo del codice sorgente si apre la propria finestra, in qualsiasi formato che sceglie, di visualizzare le differenze tra la versione più recente del file sotto controllo del codice sorgente e file dell'utente su disco.

 In alternativa, l'IDE potrebbe essere necessario semplicemente determinare se un file è stato modificato. Ad esempio, l'IDE potrebbe essere necessario determinare se è sicuro per estrarre un file senza informare l'utente. In tal caso, l'IDE passa il `SCC_DIFF_CONTENTS` flag. Il plug-in del controllo del codice sorgente deve controllare il file su disco, byte per byte, in base al file di controllo del codice sorgente e restituire un valore che indica se i due file sono diversi senza visualizzare alcun risultato all'utente.

 Ottimizzare le prestazioni, il plug-in del controllo del codice sorgente potrebbe usare un'alternativa basata su un checksum o da un timestamp anziché il confronto byte per byte chiamato da `SCC_DIFF_CONTENTS`: queste forme di confronto sono ovviamente più veloce ma meno affidabile. Non tutti i sistemi di controllo di origine possono supportare questi metodi alternativi di confronto e il plug-in potrebbe essere necessario eseguire il fallback a un confronto di contenuto. Tutti i plug-in controllo codice sorgente, è necessario come minimo, supporta un confronto di contenuto.

> [!NOTE]
> I flag di differenza rapida si escludono a vicenda. È possibile non passare alcun flag, ma non è valido passare contemporaneamente più di uno. `SCC_DIFF_QUICK_DIFF`, che è una maschera che combina tutti i flag, può essere usato per verificare, ma non deve mai essere passato come parametro.

|`fOption`|Significato|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|Confronto tra maiuscole e minuscole (può essere usato per differenza rapido o visual).|
|SCC_DIFF_IGNORESPACE|Ignora gli spazi vuoti (può essere usato per differenza rapido o visual).|
|SCC_DIFF_QD_CONTENTS|Confronta in modo invisibile il file, byte per byte.|
|SCC_DIFF_QD_CHECKSUM|Confronta in modo invisibile il file tramite un checksum quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|
|SCC_DIFF_QD_TIME|Confronta in modo invisibile il file tramite il timestamp quando è supportata. Se non è supportato, esegue il fallback a un confronto del contenuto.|

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)