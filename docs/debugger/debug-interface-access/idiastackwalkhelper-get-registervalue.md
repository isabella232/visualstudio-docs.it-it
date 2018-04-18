---
title: IDiaStackWalkHelper::get_registerValue | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::get_registerValue method
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd6aacde400309c6d0f9f78c8ec0fc540fea1428
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelpergetregistervalue"></a>IDiaStackWalkHelper::get_registerValue
Recupera il valore di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `index`  
 [in] Un valore di [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica quale registrare da cui per ottenere il valore.  
  
 `pRetVal`  
 [out] Restituisce il valore corrente del registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Nonostante la dimensione del `pRetVal` parametro un'implementazione deve archiviare solo ciò che la registrazione in genere contiene. Ad esempio, un registro a 8 bit contiene solo il più basso 8 bit del valore specificato. Questo valore a 8 bit viene espanso a 64 bit quando restituito da questo metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md)