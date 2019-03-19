---
title: 'Metodo ijsdebugdatatarget:: GetTLSValue | Microsoft Docs'
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
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157201"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>Metodo IJsDebugDataTarget::GetTlsValue
Per il thread è in corso il debug, recupera il valore nello slot di archiviazione-local (TLS) thread per l'indice TLS specificato.  
  
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
 [in] Thread in esecuzione nel processo di destinazione da cui leggere.  
  
 `tlsIndex`  
 [in] L'indice TLS che è stato allocato quando il processo di destinazione ha chiamato la funzione TlsAlloc.  
  
 `pValue`  
 [out] Il valore della dimensione del puntatore che è stato archiviato nello slot TLS del thread. Se il thread di destinazione è 32 bit, 32-bit superiori di questo valore sarà zero.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Ogni thread di un processo ha un proprio slot per ciascun indice TLS.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)