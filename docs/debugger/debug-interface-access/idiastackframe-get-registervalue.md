---
title: Get_registervalue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7799316a933e5f021df78699e41e6e9483746575
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845953"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Recupera il valore di un registro specificato archiviato nel frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `registerIndex`  
 [in] Uno dei [enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) valori di enumerazione.  
  
 `pRetVal`  
 [out] Valore archiviato nel registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumerazione CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)