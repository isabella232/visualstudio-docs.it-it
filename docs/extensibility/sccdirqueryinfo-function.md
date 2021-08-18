---
description: Questa funzione esamina un elenco di directory completo per il relativo stato corrente.
title: Funzione SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: eccf7195bfcebb83b59c8b49fd8fc430f23495dd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086378"
---
# <a name="sccdirqueryinfo-function"></a>Funzione SccDirQueryInfo
Questa funzione esamina un elenco di directory completo per il relativo stato corrente.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parametri
 pContext

[in] Struttura del contesto del plug-in del controllo del codice sorgente.

 nDirs

[in] Numero di directory selezionate su cui eseguire query.

 lpDirNames

[in] Matrice di percorsi completi delle directory su cui eseguire query.

 lpStatus

[in, out] Struttura di matrice per il plug-in di controllo del codice sorgente per restituire i flag di stato . Per informazioni dettagliate, vedere [Codice di stato della](../extensibility/directory-status-code-enumerator.md) directory.

## <a name="return-value"></a>Valore restituito
 È previsto che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituirà uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La query ha avuto esito positivo.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di problemi di connessione. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 La funzione riempie la matrice restituita con una maschera di bit di bit della famiglia (vedere Codice di stato della directory ), una voce `SCC_DIRSTATUS` per ogni directory specificata. [](../extensibility/directory-status-code-enumerator.md) La matrice di stato viene allocata dal chiamante.

 L'IDE usa questa funzione prima della ridenominazione di una directory per verificare se la directory è sotto controllo del codice sorgente tramite una query se ha un progetto corrispondente. Se la directory non è sotto controllo del codice sorgente, l'IDE può fornire l'avviso appropriato all'utente.

> [!NOTE]
> Se un plug-in del controllo del codice sorgente sceglie di non implementare uno o più valori di stato, i bit non implementati devono essere impostati su zero.

## <a name="see-also"></a>Vedi anche
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato della directory](../extensibility/directory-status-code-enumerator.md)
