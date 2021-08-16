---
description: Questa funzione inizializza il plug-in del controllo del codice sorgente e fornisce funzionalità e limiti all'ambiente di sviluppo integrato (IDE).
title: Funzione SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5d0602bd3b16b519b8fa6d0a6d42d0f882a3796a3f381007c835738846952504
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400829"
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

[in] Il plug-in del controllo del codice sorgente può inserire qui un puntatore alla struttura del contesto.

 `hWnd`

[in] Handle per la finestra IDE che il plug-in del controllo del codice sorgente può usare come elemento padre per qualsiasi finestra di dialogo fornita.

 `lpCallerName`

[in] Nome del programma che chiama il plug-in del controllo del codice sorgente.

 `lpSccName`

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce il proprio nome (da non superare `SCC_NAME_LEN` ).

 `lpSccCaps`

[out] Restituisce i flag di funzionalità del plug-in del controllo del codice sorgente.

 `lpAuxPathLabel`

[in, out] Buffer in cui il plug-in del controllo del codice sorgente inserisce una stringa che descrive il parametro restituito da `lpAuxProjPath` [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (da non superare `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

[out] Restituisce la lunghezza massima consentita per un commento di pagamento.

 `pnCommentLen`

[out] Restituisce la lunghezza massima consentita per altri commenti.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Inizializzazione del controllo del codice sorgente completata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire l'operazione specificata.|
|SCC_E_NONSPECFICERROR|Errore non specifico. Il sistema di controllo del codice sorgente non è stato inizializzato.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione quando carica per la prima volta il plug-in del controllo del codice sorgente. Consente all'IDE di passare determinate informazioni, ad esempio il nome del chiamante, al plug-in. L'IDE recupera anche determinate informazioni, ad esempio la lunghezza massima consentita per i commenti e le funzionalità del plug-in.

 Punta `ppvContext` a un `NULL` puntatore. Il plug-in del controllo del codice sorgente può allocare una struttura per il proprio utilizzo e archiviare un puntatore a tale struttura in `ppvContext` . L'IDE passerà questo puntatore a ogni altra funzione API VSSCI, consentendo al plug-in di avere informazioni sul contesto disponibili senza ricorrere all'archiviazione globale e per supportare più istanze del plug-in. Questa struttura deve essere deallocata quando viene chiamato [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 I `lpCallerName` parametri e consentono `lpSccName` all'IDE e al plug-in di controllo del codice sorgente di scambiare nomi. Questi nomi possono essere usati semplicemente per distinguere tra più istanze o possono essere effettivamente visualizzati in menu o finestre di dialogo.

 Il parametro è una stringa utilizzata come commento per identificare il percorso del progetto ausiliario archiviato nel file di soluzione e passato al plug-in del controllo del codice sorgente in una chiamata `lpAuxPathLabel` a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]usa la stringa "SourceSafe Project:"; altri plug-in del controllo del codice sorgente non devono usare questa particolare stringa.

 Il parametro fornisce al plug-in del controllo del codice sorgente una posizione in cui archiviare i flag di bit che indicano le funzionalità `lpSccCaps` del plug-in. Per un elenco completo dei flag di bit delle funzionalità, vedere [Flag di funzionalità](../extensibility/capability-flags.md). Ad esempio, se il plug-in prevede di scrivere i risultati in una funzione di callback fornita dal chiamante, il plug-in imposta il bit di SCC_CAP_TEXTOUT. Questo segnalerebbe all'IDE di creare una finestra per i risultati del controllo della versione.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
