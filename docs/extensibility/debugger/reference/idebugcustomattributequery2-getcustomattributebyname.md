---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732558"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ottiene gli attributi personalizzati byte dato il nome dell'attributo personalizzato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parametri
`pszCustomAttributeName`\
[in] Stringa contenente il nome dell'attributo personalizzato da cercare.

`ppBlob`\
[in, out] Matrice compilata con i byte dell'attributo personalizzato.

`pdwLen`\
[in, out] Specifica il numero massimo di byte `ppBlob` da restituire nella matrice e restituisce il numero di byte effettivamente scritti nella matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se l'attributo personalizzato non esiste. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Osservazioni
 Impostare `ppBlob` il parametro su un valore null per restituire il numero di byte di attributi disponibili. Quindi allocare una matrice e `ppBlob` passare tale matrice per il parametro.

 I byte dell'attributo rappresentano i dati non elaborati dell'attributo personalizzato.

 Se `ppBlob` i `pdwLen` parametri e sono impostati su un valore null, questo metodo può essere utilizzato per determinare se l'attributo personalizzato esiste semplicemente. Un'alternativa più semplice, tuttavia, consiste nel chiamare il [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
