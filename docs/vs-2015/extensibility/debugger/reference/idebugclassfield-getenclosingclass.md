---
title: 'IDebugClassField:: GetEnclosingClass | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 896d3ecd5202bf85e6b9e86af31796c662a6eef1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191002"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene la classe che racchiude questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppClassField`  
 out Restituisce un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta la classe contenitore. Restituisce un valore null se non è presente alcuna classe contenitore.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Se la classe rappresentata da questo oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) è una classe annidata, il `ppClassField` parametro restituisce un `IDebugClassField` oggetto che rappresenta la classe contenitore. Ad esempio, data questa definizione di classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 La chiamata al `GetEnclosingClass` metodo sull' `IDebugClassField` oggetto che rappresenta la `NestedClass` classe restituisce un `IDebugClassField` oggetto che rappresenta la classe `RootClass` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
