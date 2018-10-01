---
title: IDebugObject::SetValue | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c47439c69ece059b12ff0d92efd438d73a366915
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528948"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugObject::SetValue](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject-setvalue).  
  
Imposta il valore dell'oggetto da una serie consecutiva di byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pValue`  
 [in] Matrice di byte che rappresenta il nuovo valore.  
  
 `nSize`  
 [in] Le dimensioni del valore in byte.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I valori nella matrice vengono copiati [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto, sostituendo i valori esistenti. Le dimensioni del nuovo valore possono essere maggiore o minore di quello esistente. Ciò `IDebugObject` non può essere un riferimento null.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)

