---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186679"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno del relativo ambito o contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in, out] Struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) compilata da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 La struttura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) viene passata a questo metodo, che quindi la compila con le informazioni appropriate. Il modo in cui queste informazioni vengono interpretate dipende dal tipo di informazioni restituite e dal gestore di simboli stesso. Per ulteriori informazioni, vedere [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
