---
title: OPTNAMECHANGEPFN | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702242"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Si tratta di una funzione di callback specificata in una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) (opzione using `SCC_OPT_NAMECHANGEPFN` ) e viene usata per comunicare le modifiche del nome apportate dal plug-in del controllo del codice sorgente all'IDE.

## <a name="signature"></a>Firma

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

in Valore utente specificato in una chiamata precedente a [SccSetOption](../extensibility/sccsetoption-function.md) (opzione using `SCC_OPT_USERDATA` ).

 pszOldName

in Nome originale del file.

 pszNewName

in Nome in cui il file è stato rinominato.

## <a name="return-value"></a>Valore restituito
 No.

## <a name="remarks"></a>Osservazioni
 Se un file viene rinominato durante un'operazione del controllo del codice sorgente, il plug-in del controllo del codice sorgente può notificare all'IDE la modifica del nome tramite questo callback.

 Se l'IDE non supporta questo callback, non chiamerà [SccSetOption](../extensibility/sccsetoption-function.md) per specificarlo. Se il plug-in non supporta questo callback, viene restituito `SCC_E_OPNOTSUPPORTED` dalla `SccSetOption` funzione quando l'IDE tenta di impostare il callback.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
