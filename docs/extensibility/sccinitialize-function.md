---
title: Funzione SccInitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 552ec06a4eabf55872358fc8e5d731e47c1eb6ca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721177"
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

[in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce il proprio nome (senza superare `SCC_NAME_LEN`).

 `lpSccCaps`

out Restituisce i flag di capacità del plug-in del controllo del codice sorgente.

 `lpAuxPathLabel`

[in, out] Il buffer in cui il plug-in del controllo del codice sorgente inserisce una stringa che descrive il parametro `lpAuxProjPath` restituito da [SccOpenProject](../extensibility/sccopenproject-function.md) e [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (senza superare `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

out Restituisce la lunghezza massima consentita per un commento di estrazione.

 `pnCommentLen`

out Restituisce la lunghezza massima consentita per altri commenti.

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Inizializzazione del controllo del codice sorgente completata.|
|SCC_E_INITIALIZEFAILED|Impossibile inizializzare il sistema.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire l'operazione specificata.|
|SCC_E_NONSPECFICERROR|Errore non specifico. sistema di controllo del codice sorgente non inizializzato.|

## <a name="remarks"></a>Note
 L'IDE chiama questa funzione al primo caricamento del plug-in del controllo del codice sorgente. Consente all'IDE di passare al plug-in determinate informazioni, ad esempio il nome del chiamante. L'IDE restituisce anche alcune informazioni, ad esempio la lunghezza massima consentita per i commenti e le funzionalità del plug-in.

 Il `ppvContext` punta a un puntatore di `NULL`. Il plug-in del controllo del codice sorgente può allocare una struttura per uso personale e archiviare un puntatore a tale struttura in `ppvContext`. L'IDE passerà questo puntatore a ogni altra funzione API VSSCI, consentendo al plug-in di disporre di informazioni di contesto disponibili senza ricorrere all'archiviazione globale e supportare più istanze del plug-in. Questa struttura deve essere deallocata quando viene chiamato [SccUninitialize](../extensibility/sccuninitialize-function.md) .

 I parametri `lpCallerName` e `lpSccName` consentono all'IDE e al plug-in del controllo del codice sorgente di scambiare i nomi. Questi nomi possono essere utilizzati semplicemente per distinguere tra più istanze oppure possono essere effettivamente visualizzati nei menu o nelle finestre di dialogo.

 Il parametro `lpAuxPathLabel` è una stringa utilizzata come commento per identificare il percorso del progetto ausiliario archiviato nel file della soluzione e passato al plug-in del controllo del codice sorgente in una chiamata a [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] utilizza la stringa "progetto SourceSafe:"; altri plug-in del controllo del codice sorgente devono evitare di usare questa particolare stringa.

 Il parametro `lpSccCaps` fornisce al plug-in del controllo del codice sorgente una posizione per archiviare flag che indica le funzionalità del plug-in. Per un elenco completo delle funzionalità flag, vedere [flag funzionalità](../extensibility/capability-flags.md). Se, ad esempio, il plug-in prevede di scrivere i risultati in una funzione di callback fornita dal chiamante, il plug-in imposterà il bit di funzionalità SCC_CAP_TEXTOUT. Questo segnalerebbe all'IDE di creare una finestra per i risultati del controllo della versione.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Flag di funzionalità](../extensibility/capability-flags.md)