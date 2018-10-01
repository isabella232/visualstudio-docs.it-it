---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
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
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b29b6eb411c511612b60faf271d23decd7370c12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528532"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugObject2::GetBackingFieldForProperty](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty).  
  
Ottiene il campo o una variabile (se presente) che può essere supporta la proprietà rappresentata da questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppObject`  
 [out] Un' [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto che descrive il campo sottostante.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) oggetto rappresenta una proprietà di classe di codice gestito, vale a dire, un metodo con una richiesta get e/o funzione di accesso set. Tali proprietà richiedono in genere una variabile per contenere il valore modificato dalla proprietà. Questa variabile è noto come il campo sottostante. Se è presente alcun campo sottostante per l'oggetto, quindi assicurarsi di restituire un valore null: alcuni chiamanti potrebbero non prestare attenzione al valore restituito, ma avrà un aspetto invece per vedere se è stato restituito un valore null in `ppObject`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

