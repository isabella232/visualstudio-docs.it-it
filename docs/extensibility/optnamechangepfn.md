---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: Informazioni sulla funzione di callback OPTNAMECHANGEPFN, che comunica le modifiche dei nomi dal plug-in del controllo del codice sorgente all'IDE Visual Studio codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ecd4682058bfb024db55658d88d0e629a40881b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094516"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Si tratta di una funzione di callback specificata in una chiamata a [SccSetOption](../extensibility/sccsetoption-function.md) (usando l'opzione ) e viene usata per comunicare le modifiche dei nomi apportate dal plug-in del controllo del codice sorgente `SCC_OPT_NAMECHANGEPFN` all'IDE.

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

[in] Valore utente specificato in una chiamata precedente a [SccSetOption](../extensibility/sccsetoption-function.md) (usando l'opzione `SCC_OPT_USERDATA` ).

 pszOldName

[in] Nome originale del file.

 pszNewName

[in] Nome in cui è stato rinominato il file.

## <a name="return-value"></a>Valore restituito
 No.

## <a name="remarks"></a>Osservazioni
 Se un file viene rinominato durante un'operazione di controllo del codice sorgente, il plug-in del controllo del codice sorgente può notificare all'IDE la modifica del nome tramite questo callback.

 Se l'IDE non supporta questo callback, non chiamerà [SccSetOption](../extensibility/sccsetoption-function.md) per specificarlo. Se il plug-in non supporta questo callback, verrà restituito dalla funzione quando `SCC_E_OPNOTSUPPORTED` l'IDE tenta di impostare il `SccSetOption` callback.

## <a name="see-also"></a>Vedi anche
- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
