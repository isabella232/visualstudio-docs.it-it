---
title: IDebugCodeContext2::GetLanguageInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 465cc07b3ca75835afe0737fb22ba403acc4098b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734237"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ottiene le informazioni sul linguaggio per questo contesto di codice.

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

## <a name="parameters"></a>Parametri
`pbstrLanguage`\
[in, out] Restituisce una stringa che contiene il nome della lingua, ad esempio "C" .

`pguidLanguage`\
[in, out] Restituisce il GUID per la lingua del `guidCPPLang`contesto del codice, ad esempio .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Almeno uno dei parametri deve restituire un valore non null.

## <a name="see-also"></a>Vedere anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
