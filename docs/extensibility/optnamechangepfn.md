---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32d173925d8970ec6be0872c8260d1d6219625fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433487"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Si tratta di una funzione di callback specificata in una chiamata ai [SccSetOption](../extensibility/sccsetoption-function.md) (tramite opzione `SCC_OPT_NAMECHANGEPFN`) e viene usato per comunicare modifiche ai nomi effettuate dal controllo del codice sorgente del plug-in dell'IDE di.

## <a name="signature"></a>Signature

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parametri
 pvCallerData

[in] Valore utente specificato in una chiamata precedente al [SccSetOption](../extensibility/sccsetoption-function.md) (tramite opzione `SCC_OPT_USERDATA`).

 pszOldName

[in] Il nome originale del file.

 pszNewName

[in] Il nome del file è stato rinominato in.

## <a name="return-value"></a>Valore restituito
 Nessuno.

## <a name="remarks"></a>Note
 Se un file viene rinominato durante un'operazione di controllo del codice sorgente, il plug-in del controllo del codice sorgente può notificare l'IDE di modifica del nome tramite questo callback.

 Se l'IDE non supporta questo callback, non chiamerà il [SccSetOption](../extensibility/sccsetoption-function.md) specificarlo. Se il plug-in non supporta questo callback, restituirà `SCC_E_OPNOTSUPPORTED` dal `SccSetOption` corretto quando l'IDE tenta di impostare il callback.

## <a name="see-also"></a>Vedere anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)