---
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ed4e1863313dae173d6737970765ca3d5f0b0b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879454"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Questo metodo recupera un elenco dei tipi di argomento associato all'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `skip`  
 [in] Numero di campi da ignorare prima di ottenere i tipi di argomento.  
  
 `count`  
 [in] Il numero di campi dell'argomento da restituire (specifica anche la dimensione del `ppFields` matrice).  
  
 `ppFields`  
 [in, out] Matrice di campi che verranno compilati in fase di restituzione di questo metodo.  
  
 `pFetched`  
 [out] \(facoltativo) Il numero di argomenti tipo campi effettivamente restituiti.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 È possibile ottenere in anticipo il numero di tipi di argomento con [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)