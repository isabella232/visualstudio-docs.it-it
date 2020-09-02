---
title: 'IDebugMethodField:: EnumLocals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2306bbf0c44a883c584346c3dbb3dd70e9b39175
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162607"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per le variabili locali selezionate del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 in Oggetto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) che rappresenta l'indirizzo di debug che seleziona il contesto o l'ambito da cui ottenere le variabili locali.  
  
 `ppLocals`  
 out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta un elenco di variabili locali. in caso contrario, restituisce un valore null se non sono presenti variabili locali.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Vengono enumerate solo le variabili definite all'interno del blocco che contiene l'indirizzo di debug specificato. Se sono necessarie tutte le variabili locali, incluse quelle generate dal compilatore, chiamare il metodo [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) .  
  
 Un metodo può contenere più contesti di ambito o blocchi. Il metodo escogitato seguente, ad esempio, contiene tre ambiti, i due blocchi interni e il corpo del metodo stesso.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 L'oggetto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) rappresenta il `func` metodo stesso. Se si chiama il `EnumLocals` metodo con un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) impostato sull' `Inner Scope 1` Indirizzo, viene restituita un'enumerazione che contiene la `temp1` variabile, ad esempio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
