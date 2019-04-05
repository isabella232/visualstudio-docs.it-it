---
title: IDebugMethodField::EnumAllLocals | Microsoft Docs
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
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58963867"
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
 [in] Un' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) oggetto che rappresenta un indirizzo di debug all'interno del metodo, che punta a un ambito specifico o di contesto.  
  
 `ppLocals`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) rappresentano l'elenco di tutte le variabili locali nell'ambito specificato dell'oggetto; in caso contrario, restituisce un valore null indicante che nessuna variabile locale.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se non sono variabili non locali. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Questo metodo include le variabili locali generate dal compilatore. Se tutto ciò che serve sono variabili locali definite in modo esplicito nell'origine, chiamata di [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) (metodo).  
  
 Un metodo può contenere più blocchi o i contesti di definizione dell'ambito.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
