---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 7884bff62321ed07c3a11a6db65855b1edea0adc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688407"
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
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)