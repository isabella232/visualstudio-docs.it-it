---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e82f2d1635b46dccd9f5f93b5773ba757342f04d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838998"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene l'oggetto puntato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwIndex`  
 [in] Un offset di byte semplici dall'inizio dell'oggetto puntato.  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) dell'oggetto che rappresenta l'oggetto a cui, oltre a eseguire l'offset, se presente.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore. Restituisce E_FAIL se questo oggetto non fa riferimento a un altro oggetto.  
  
## <a name="remarks"></a>Note  
 L'oggetto a cui può essere primitivo o un tipo più complesso, ad esempio una classe o struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)

