---
title: IDebugClassField::GetEnclosingClass | Microsoft Docs
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
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34648ee01b1aaa070dea779777095bda98133211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518793"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugClassField::GetEnclosingClass](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugclassfield-getenclosingclass).  
  
Ottiene la classe che comprende questa classe.  
  
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
 [out] Restituisce un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) classe oggetto che rappresenta il tipo di inclusione. Restituisce un valore null se nessuna classe che lo contiene.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se la classe rappresentata da questo [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto è una classe annidata, il `ppClassField` parametro restituisce un `IDebugClassField` classe oggetto che rappresenta il tipo di inclusione. Ad esempio, Data questa definizione di classe:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Chiama il `GetEnclosingClass` metodo sul `IDebugClassField` oggetto che rappresenta il `NestedClass` classe restituisce un' `IDebugClassField` oggetto che rappresenta la classe `RootClass`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)

