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
ms.openlocfilehash: 31f46f8b392d5d3b37aed91a6867d80835be0d23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963918"
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
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)