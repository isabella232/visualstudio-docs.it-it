---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4afcb2a8fd9de89b74fccec373e71e19264fe56
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712489"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ottiene le informazioni sulla lingua per il contesto di codice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

#### <a name="parameters"></a>Parametri
 `pbstrLanguage`

 [in, out] Restituisce una stringa che contiene il nome del linguaggio, ad esempio "C++".

 `pguidLanguage`

 [in, out] Restituisce il GUID per la lingua del contesto del codice, ad esempio, `guidCPPLang`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Almeno uno dei parametri deve restituire un valore diverso da null.

## <a name="see-also"></a>Vedere anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)