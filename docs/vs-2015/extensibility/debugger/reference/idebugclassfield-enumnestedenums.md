---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84f60b9b0c882883c930657df59530f1c5107a22
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191067"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per gli enumeratori annidati di questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
