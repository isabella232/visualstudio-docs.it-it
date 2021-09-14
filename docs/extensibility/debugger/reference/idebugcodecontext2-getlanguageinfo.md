---
description: Ottiene le informazioni sulla lingua per questo contesto del codice.
title: Interfaccia IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1f3c2ac4eb0a41e94415ab83605f978e691311d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627444"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Ottiene le informazioni sulla lingua per questo contesto del codice.

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
[in, out] Restituisce una stringa che contiene il nome del linguaggio, ad esempio "C++".

`pguidLanguage`\
[in, out] Restituisce il GUID per il linguaggio del contesto del codice, ad esempio `guidCPPLang` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Almeno uno dei parametri deve restituire un valore non Null.

## <a name="see-also"></a>Vedi anche
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
