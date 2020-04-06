---
title: Funzione SccInitialize . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700638"
---
# <a name="sccinitialize-function"></a>Funzione SccInitialize
Questa funzione inizializza il plug-in del controllo del codice sorgente e fornisce funzionalità e limiti all'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parametri
 `ppvContext`

[in] Il plug-in del controllo del codice sorgente può inserire un puntatore alla relativa struttura di contesto qui.

 `hWnd`

[in] Un handle per la finestra dell'IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo che fornisce.

 `lpCallerName`

[in] Nome del programma che chiama il plug-in del controllo del codice sorgente.

 `lpSccName`

[in, out] Il buffer in cui il plug-in del controllo `SCC_NAME_LEN`del codice sorgente inserisce il proprio nome (non superare ).

 `lpSccCaps`

[fuori] Restituisce i flag di funzionalità del plug-in del controllo del codice sorgente.

 `lpAuxPathLabel`

[in, out] Buffer in cui il plug-in del controllo `lpAuxProjPath` del codice sorgente inserisce una stringa che descrive il parametro restituito da [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (non superare `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

[fuori] Restituisce la lunghezza massima consentita per un commento di checkout.

 `pnCommentLen`

[fuori] Restituisce la lunghezza massima consentita per altri commenti.

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Inizializzazione del controllo del codice sorgente riuscita.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema.|
|SCC_E_NOTAUTHORIZED|All'utente non è consentito eseguire l'operazione specificata.|
|SCC_E_NONSPECFICERROR|Errore non specifico; sistema di controllo del codice sorgente non è stato inizializzato.|

## <a name="remarks"></a>Osservazioni
 L'IDE chiama questa funzione quando carica per la prima volta il plug-in del controllo del codice sorgente. Consente all'IDE di passare determinate informazioni, ad esempio il nome del chiamante, al plug-in. L'IDE ottiene anche alcune informazioni, ad esempio la lunghezza massima consentita per i commenti e le funzionalità del plug-in.

 Punta `ppvContext` il `NULL` puntatore su un puntatore. Il plug-in del controllo del codice sorgente può allocare una `ppvContext`struttura per il proprio utilizzo e archiviare un puntatore a tale struttura in . L'IDE passerà questo puntatore a ogni altra funzione API VSSCI, consentendo al plug-in di avere informazioni sul contesto disponibili senza ricorrere all'archiviazione globale e per supportare più istanze del plug-in. Questa struttura deve essere deallocata quando il [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.

 I `lpCallerName` `lpSccName` parametri e abilitano l'IDE e il plug-in del controllo del codice sorgente per lo scambio di nomi. Questi nomi possono essere utilizzati semplicemente per distinguere tra più istanze, o possono effettivamente apparire nei menu o nelle finestre di dialogo.

 Il `lpAuxPathLabel` parametro è una stringa utilizzata come commento per identificare il percorso del progetto ausiliario archiviato nel file di soluzione e passato al plug-in del controllo del codice sorgente in una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]utilizza la stringa "Progetto SourceSafe:"; altri plug-in del controllo del codice sorgente devono astenersi dall'utilizzo di questa particolare stringa.

 Il `lpSccCaps` parametro fornisce al plug-in del controllo del codice sorgente una posizione in cui archiviare i flag di bit che indicano le funzionalità del plug-in. Per un elenco completo dei flag di bit di funzionalità, vedere [Flag di funzionalità](../extensibility/capability-flags.md). Ad esempio, se il plug-in prevede di scrivere i risultati in una funzione di callback fornita dal chiamante, il plug-in imposterà il bit di funzionalità SCC_CAP_TEXTOUT. Ciò segnalerebbe l'IDE per creare una finestra per i risultati del controllo della versione.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
