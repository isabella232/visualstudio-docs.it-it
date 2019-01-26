---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adddb92adc7f62d51efd5c87ad40c1f47de41ae7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040723"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se un'interfaccia specifica viene definita nella classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```csharp  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszInterfaceName`  
 [in] Stringa contenente il nome dell'interfaccia da cercare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK, restituisce S_FALSE se l'interfaccia non esiste. in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In effetti, questo metodo ottiene un'enumerazione di tutte le interfacce e Cerca nell'elenco per un'interfaccia corrisponda.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)