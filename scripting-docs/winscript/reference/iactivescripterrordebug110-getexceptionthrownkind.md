---
title: IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a58add60560f22681f18225d844814e3547b671f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436064"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Restituisce un valore che indica il tipo di eccezione generata.  
  
> [!IMPORTANT]
> [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md) viene implementata da PDM versioni 11.0 e successiva. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExceptionKind`  
 [out] Il tipo di eccezione che viene generata un'eccezione (ad esempio, first-chance o non gestita), rappresentato da un [enumerazione SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) valore di enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)