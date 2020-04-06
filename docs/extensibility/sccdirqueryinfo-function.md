---
title: SccDirQueryInfo (funzione) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700956"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo (funzione)SccDirQueryInfo function
Questa funzione esamina un elenco di directory complete per il relativo stato corrente.

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

[in] Struttura di contesto del plug-in del controllo del codice sorgente.

 nDirs (informazioni in stato infondi)

[in] Il numero di directory selezionate per la query.

 lpDirNames (Nomi dei nomi lpDir)

[in] Matrice di percorsi completi delle directory su cui eseguire la query.

 lpStatus (Stato

[in, out] Struttura della matrice per il plug-in del controllo del codice sorgente per restituire i flag di stato (per informazioni dettagliate, vedere Codice di [stato della directory).](../extensibility/directory-status-code-enumerator.md)

## <a name="return-value"></a>Valore restituito
 L'implementazione del plug-in del controllo del codice sorgente di questa funzione deve restituire uno dei seguenti valori:

|valore|Descrizione|
|-----------|-----------------|
|SCC_OK|La query ha avuto esito positivo.|
|SCC_E_OPNOTSUPPORTED|Il sistema di controllo del codice sorgente non supporta questa operazione.|
|SCC_E_ACCESSFAILURE|Si è verificato un problema durante l'accesso al sistema di controllo del codice sorgente, probabilmente a causa di problemi di rete o di contesa. È consigliabile eseguire un nuovo tentativo.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Osservazioni
 La funzione riempie la matrice return con una `SCC_DIRSTATUS` maschera di bit di bit della famiglia (vedere Codice di [stato della directory](../extensibility/directory-status-code-enumerator.md)), una voce per ogni directory specificata. La matrice di stato viene allocata dal chiamante.

 L'IDE utilizza questa funzione prima che una directory viene rinominata per verificare se la directory è sotto controllo del codice sorgente eseguendo una query se dispone di un progetto corrispondente. Se la directory non è in controllo del codice sorgente, l'IDE può fornire l'avviso corretto per l'utente.

> [!NOTE]
> Se un plug-in del controllo del codice sorgente sceglie di non implementare uno o più valori di stato, i bit non implementati devono essere impostati su zero.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
- [Codice di stato della directory](../extensibility/directory-status-code-enumerator.md)
