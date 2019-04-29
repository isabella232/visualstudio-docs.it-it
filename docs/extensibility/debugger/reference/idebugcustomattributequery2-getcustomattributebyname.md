---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e6275f67e07c88cb337c77bc672394af539b8e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875946"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Ottiene i byte di attributi personalizzati, dato il nome dell'attributo personalizzato.

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

#### <a name="parameters"></a>Parametri
 `pszCustomAttributeName`

 [in] Stringa contenente il nome dell'attributo personalizzato da cercare.

 `ppBlob`

 [in, out] Matrice che viene compilata con i byte di attributo personalizzato.

 `pdwLen`

 [in, out] Specifica il numero massimo di byte da restituire nel `ppBlob` della matrice e restituisce il numero di byte effettivamente scritti nella matrice.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK o restituisce S_FALSE se l'attributo personalizzato non esiste. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Note
 Impostare il `ppBlob` attributi di parametro con un valore null per restituire il numero di byte disponibili. Quindi allocare una matrice e passare la matrice in per il `ppBlob` parametro.

 I byte di attributo rappresentano i dati non elaborati dell'attributo personalizzato.

 Se il `ppBlob` e `pdwLen` parametri vengono impostati su un valore null, questo metodo può essere utilizzato per determinare se esiste semplicemente l'attributo personalizzato. Un'alternativa più semplice, tuttavia, consiste nel chiamare il [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)