---
title: IDebugGenericFieldInstance::GetTypeArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTypeArguments
- IDebugGenericFieldInstance::GetTypeArguments
ms.assetid: 6e7e0f95-181a-4805-adb3-c2407de0ab93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a41c4b568e6cd9423a39907ebb3ba581aaf8b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024591"
---
# <a name="idebuggenericfieldinstancegettypearguments"></a>IDebugGenericFieldInstance::GetTypeArguments
Recupera gli argomenti di parametro di tipo per questa istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeArguments(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   ULONG32*      pcArgs  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint              cArgs,  
   out IDebugField[] ppArgs,  
   ref uint          pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cArgs`  
 [in] Numero di parametri di tipo.  
  
 `ppArgs`  
 [out] Restituisce una matrice di parametri di tipo.  
  
 `pcArgs`  
 [in, out] Numero di membri di `ppArgs` matrice.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)