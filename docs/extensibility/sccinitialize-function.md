---
title: Funzione SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9fb944cb672249ecb823f48048d12c1b61d9e99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846361"
---
# <a name="sccinitialize-function"></a>Funzione SccInitialize
Questa funzione Inizializza il plug-in del controllo del codice sorgente e fornisce le funzionalità e i limiti per il Integrated Development Environment (IDE).

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

in Il plug-in del controllo del codice sorgente può inserire qui un puntatore alla struttura del contesto.

 `hWnd`

in Handle per la finestra IDE che il plug-in del controllo del codice sorgente può utilizzare come elemento padre per tutte le finestre di dialogo fornite.

 `lpCallerName`

in Nome del programma che chiama il plug-in del controllo del codice sorgente.

 `lpSccName`

[in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce il proprio nome (senza superare `SCC_NAME_LEN` ).

 `lpSccCaps`

out Restituisce i flag di capacità del plug-in del controllo del codice sorgente.

 `lpAuxPathLabel`

[in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce una stringa che descrive il `lpAuxProjPath` parametro restituito da [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (senza superare `SCC_AUXLABEL_LEN` ).

 `pnCheckoutCommentLen`

out Restituisce la lunghezza massima consentita per un commento di estrazione.

 `pnCommentLen`

out Restituisce la lunghezza massima consentita per altri commenti.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Inizializzazione del controllo del codice sorgente completata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire l'operazione specificata.|
|SCC_E_NONSPECFICERROR|Errore non specifico. sistema di controllo del codice sorgente non inizializzato.|

## <a name="remarks"></a>Commenti
 L'IDE chiama questa funzione al primo caricamento del plug-in del controllo del codice sorgente. Consente all'IDE di passare al plug-in determinate informazioni, ad esempio il nome del chiamante. L'IDE restituisce anche alcune informazioni, ad esempio la lunghezza massima consentita per i commenti e le funzionalità del plug-in.

 `ppvContext`Punta a un `NULL` puntatore. Il plug-in del controllo del codice sorgente può allocare una struttura per uso personale e archiviare un puntatore a tale struttura in `ppvContext` . L'IDE passerà questo puntatore a ogni altra funzione API VSSCI, consentendo al plug-in di disporre di informazioni di contesto disponibili senza ricorrere all'archiviazione globale e supportare più istanze del plug-in. Questa struttura deve essere deallocata quando viene chiamato [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 I `lpCallerName` `lpSccName` parametri e consentono all'IDE e al plug-in del controllo del codice sorgente di scambiare i nomi. Questi nomi possono essere utilizzati semplicemente per distinguere tra più istanze oppure possono essere effettivamente visualizzati nei menu o nelle finestre di dialogo.

 Il `lpAuxPathLabel` parametro è una stringa utilizzata come commento per identificare il percorso del progetto ausiliario archiviato nel file della soluzione e passato al plug-in del controllo del codice sorgente in una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] Usa la stringa "progetto SourceSafe:"; altri plug-in del controllo del codice sorgente devono evitare di usare questa particolare stringa.

 Il `lpSccCaps` parametro fornisce al plug-in del controllo del codice sorgente una posizione per archiviare flag che indica le funzionalità del plug-in. Per un elenco completo delle funzionalità flag, vedere [flag funzionalità](../extensibility/capability-flags.md). Se, ad esempio, il plug-in prevede di scrivere i risultati in una funzione di callback fornita dal chiamante, il plug-in imposterà il bit di capacità SCC_CAP_TEXTOUT. Questo segnalerebbe all'IDE di creare una finestra per i risultati del controllo della versione.

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)
