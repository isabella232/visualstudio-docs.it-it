---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 941417adad62b7a09abc1515800a9200baf0bfcb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939042"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Recupera un'interfaccia di codice gestito che rappresenta il valore associato a questo alias.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUnk`  
 [out] `IUnknown` interfaccia che rappresenta il valore associato a questo alias. Questa interfaccia è possibile eseguire query per il `ICorDebugValue` interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo si applica solo ai valori gestiti (il `ICorDebugValue` è disponibile in un'interfaccia di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] e viene definito nel [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK nel file Cordebug. idl).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)