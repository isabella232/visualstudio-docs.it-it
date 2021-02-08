---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8662e3c18f568e60ac98e5468acc3da28966505c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842446"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ottiene i byte degli attributi personalizzati in base al nome dell'attributo personalizzato.

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
in Stringa che contiene il nome dell'attributo personalizzato di cui eseguire la ricerca.

`ppBlob`\
[in, out] Matrice compilata con i byte dell'attributo personalizzato.

`pdwLen`\
[in, out] Specifica il numero massimo di byte da restituire nella `ppBlob` matrice e restituisce il numero di byte effettivamente scritti nella matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se l'attributo personalizzato non esiste. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Impostare il `ppBlob` parametro su un valore null per restituire il numero di byte degli attributi disponibili. Quindi allocare una matrice e passare la matrice in per il `ppBlob` parametro.

 I byte degli attributi rappresentano i dati non elaborati dell'attributo personalizzato.

 Se i `ppBlob` `pdwLen` parametri e sono impostati su un valore null, questo metodo può essere utilizzato per determinare se l'attributo personalizzato esiste semplicemente. Un'alternativa più semplice è, tuttavia, chiamare il metodo [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
