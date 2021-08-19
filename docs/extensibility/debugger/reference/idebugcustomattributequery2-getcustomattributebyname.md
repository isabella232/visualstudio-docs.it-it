---
description: Ottiene i byte degli attributi personalizzati in base al nome dell'attributo personalizzato.
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e20f4cba0d826a7a9b608f1fc56fde1a35ae54c0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079415"
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
[in] Stringa contenente il nome dell'attributo personalizzato da cercare.

`ppBlob`\
[in, out] Matrice compilata con i byte dell'attributo personalizzato.

`pdwLen`\
[in, out] Specifica il numero massimo di byte da restituire nella matrice e restituisce il `ppBlob` numero di byte effettivamente scritti nella matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK o restituisce S_FALSE se l'attributo personalizzato non esiste. In caso contrario, verrà restituito un codice di errore.

## <a name="remarks"></a>Commenti
 Impostare il `ppBlob` parametro su un valore Null per restituire il numero di byte di attributi disponibili. Allocare quindi una matrice e passare tale matrice in per il `ppBlob` parametro .

 I byte dell'attributo rappresentano i dati non elaborati dell'attributo personalizzato.

 Se i parametri e sono impostati su un valore Null, questo metodo può essere usato per determinare se `ppBlob` `pdwLen` l'attributo personalizzato esiste semplicemente. Un'alternativa più semplice, tuttavia, consiste nel chiamare il [metodo IsCustomAttributeDefined.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Vedi anche
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
