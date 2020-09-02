---
title: 'IDebugMethodField:: EnumStaticLocals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumStaticLocals
helpviewer_keywords:
- IDebugMethodField::EnumStaticLocals method
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 69230ce3f748cca460c08d2d40648523161707d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162578"
---
# <a name="idebugmethodfieldenumstaticlocals"></a>IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per le variabili locali statiche del metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppLocals`  
 out Restituisce un oggetto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) che rappresenta l'elenco di variabili locali statiche. Restituisce un valore null se non sono presenti variabili locali statiche.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se non sono presenti variabili locali statiche. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Ogni elemento è un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta tipi diversi di variabili locali statiche. Chiamare il metodo [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) su ogni oggetto per determinare esattamente il tipo di locale statico rappresentato dall'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
