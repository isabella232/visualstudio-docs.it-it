---
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 67ab8a7343cd320470515b757dfca905a0a4690e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968006"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Questo metodo si applica solo ai valori gestiti (il `ICorDebugValue` è disponibile in un'interfaccia di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] e viene definito nel [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK nel file Cordebug. idl).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
