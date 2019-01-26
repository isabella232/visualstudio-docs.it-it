---
title: IDebugDefaultPort2::QueryIsLocal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad9fb8381509ffbdabb4968f35c6b23c461d70e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038643"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Questo metodo determina se questa porta è nel computer locale.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se questa porta è locale (nello stesso computer del chiamante) o `S_FALSE` se la porta è in un altro computer.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)