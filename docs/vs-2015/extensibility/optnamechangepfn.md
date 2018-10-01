---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f729e00805fa1c73fe1e64197788dd31f2a2a41d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517182"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [OPTNAMECHANGEPFN](https://docs.microsoft.com/visualstudio/extensibility/optnamechangepfn).  
  
Si tratta di una funzione di callback specificata in una chiamata ai [SccSetOption](../extensibility/sccsetoption-function.md) (tramite opzione `SCC_OPT_NAMECHANGEPFN`) e viene usato per comunicare modifiche ai nomi effettuate dal controllo del codice sorgente del plug-in dell'IDE di.  
  
## <a name="signature"></a>Signature  
  
```cpp#  
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

