---
title: 'Metodo metodo ijsdebugdatatarget:: GetTlsValue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577600"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Metodo IJsDebugDataTarget::GetTlsValue
Per il thread di cui è in corso il debug, recupera il valore nello slot TLS (thread local storage) per l'indice TLS specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 in Thread in esecuzione nel processo di destinazione da cui leggere.  
  
 `tlsIndex`  
 in Indice TLS allocato quando il processo di destinazione ha chiamato la funzione TlsAlloc.  
  
 `pValue`  
 out Valore di dimensioni del puntatore che è stato archiviato nello slot TLS del thread. Se il thread di destinazione è a 32 bit, il 32 bit superiore di questo valore sarà zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Ogni thread di un processo ha il proprio slot per ogni indice TLS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)