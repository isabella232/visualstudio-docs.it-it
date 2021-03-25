---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: Informazioni sulla funzione di callback OPTNAMECHANGEPFN, che comunica le modifiche dei nomi dal plug-in del controllo del codice sorgente all'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4e6cb58aebbe76eff5c66dc29ecfad8c77c8717c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090369"
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

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
