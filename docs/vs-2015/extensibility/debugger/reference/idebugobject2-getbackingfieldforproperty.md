---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5eadbed61638ff1442c4ed7033426e245abf930a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62536386"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il campo o la variabile, se presente, che può eseguire il backup della proprietà rappresentata da questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 out Oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) che descrive il campo sottostante.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) rappresenta una proprietà della classe di codice gestito, ovvero un metodo con una funzione di accesso get e/o set. Tali proprietà richiedono in genere una variabile per contenere il valore modificato dalla proprietà. Questa variabile è nota come campo sottostante. Se non è presente alcun campo di supporto per l'oggetto, assicurarsi di restituire un valore null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma cercheranno invece di verificare se è stato restituito un valore null in `ppObject` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
