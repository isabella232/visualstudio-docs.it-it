---
title: 'IDebugMethodField:: EnumAllLocals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f0f89c3fee45d6d56b845753958d697e41ab11f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190881"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per tutte le variabili locali del metodo, inclusi quelli generati internamente da un compilatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 in Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) che rappresenta un indirizzo di debug all'interno del metodo, che punta a un ambito o a un contesto specifico.  
  
 `ppLocals`  
 out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di tutte le variabili locali nell'ambito specificato. in caso contrario, restituisce un valore null che indica l'assenza di variabili locali.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Questo metodo include le variabili locali generate dal compilatore. Se sono necessarie tutte le variabili locali definite in modo esplicito nell'origine, chiamare il metodo [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .  
  
 Un metodo può contenere più contesti di ambito o blocchi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
