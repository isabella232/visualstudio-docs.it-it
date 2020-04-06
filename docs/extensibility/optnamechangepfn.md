---
title: METODO OPTNAMECHANGEPFN . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702242"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Si tratta di una funzione di callback specificata in `SCC_OPT_NAMECHANGEPFN`una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) (utilizzando l'opzione ) e viene utilizzata per comunicare all'IDE le modifiche apportate al nome apportate dal plug-in del controllo del codice sorgente.

## <a name="signature"></a>Firma

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData (informazioni in fibra con i dati)

[in] Valore utente specificato in una precedente chiamata a `SCC_OPT_USERDATA` [SccSetOption](../extensibility/sccsetoption-function.md) (utilizzando l'opzione ).

 pszOldName (nome spzOldName)

[in] Nome originale del file.

 pszNewName (nome di dominio spzNewName)

[in] Nome con cui è stato rinominato il file.

## <a name="return-value"></a>Valore restituito
 No.

## <a name="remarks"></a>Osservazioni
 Se un file viene rinominato durante un'operazione del controllo del codice sorgente, il plug-in del controllo del codice sorgente può notificare all'IDE la modifica del nome tramite questo callback.

 Se l'IDE non supporta questo callback, non chiamerà [sccSetOption](../extensibility/sccsetoption-function.md) per specificarlo. Se il plug-in non supporta questo `SCC_E_OPNOTSUPPORTED` callback, `SccSetOption` restituirà dalla funzione quando l'IDE tenta di impostare il callback.

## <a name="see-also"></a>Vedere anche
- [Callback functions implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
