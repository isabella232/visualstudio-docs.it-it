---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8d440783dbd6112e6f9918cd22388b4b8efbff0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921190"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Questo metodo in modo esplicito Disabilita modifica e continuazione su questo processo (e tutti i programmi contengono). Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `reason`  
 [in] Un valore compreso il [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
> [!NOTE]
>  Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
 Una volta modifica e continuazione è disabilitata per un processo, può essere abilitato nuovamente solo riavviando il processo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)