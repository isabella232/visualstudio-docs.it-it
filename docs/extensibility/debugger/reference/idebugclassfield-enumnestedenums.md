---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c033246d27cd640e760b8dfd06e65ee1b2b8cfbb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038175"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
Crea un enumeratore per gli enumeratori annidati di questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco delle enumerazioni annidate. Restituisce un valore null se non esistono Nessun enumerazioni annidate.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non esistono Nessun enumeratori annidati. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni elemento dell'enumerazione è un [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) oggetto che descrive un'enumerazione nidificata.  
  
 Un'enumerazione dichiarata all'interno di una classe è considerata un'enumerazione nidificata. Ad esempio, dato:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 Il `EnumNestedEnums` metodo restituirebbe un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che contiene uno [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) oggetto che rappresenta il `NestedEnum` enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)