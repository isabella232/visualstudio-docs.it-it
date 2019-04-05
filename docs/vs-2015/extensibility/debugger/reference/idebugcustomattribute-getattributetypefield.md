---
title: IDebugCustomAttribute::GetAttributeTypeField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a56a148342eb659a4f57d68581159f64ee3b1226
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966692"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il tipo di classe di attributo personalizzato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppCAType`  
 [out] Restituisce il [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) oggetto che rappresenta la classe di cui l'attributo personalizzato è un'istanza.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un attributo personalizzato è sempre una classe. Questo metodo fornisce l'accesso a un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che descrive tale classe.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
