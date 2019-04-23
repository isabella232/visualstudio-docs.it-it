---
title: IDebugStackFrame2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d0f5c17fc0dd12cf8ecb184b667880462548877
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093280"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Ottiene la lingua associata a questo frame dello stack.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

#### <a name="parameters"></a>Parametri
 `pbstrLanguage`

 [out] Restituisce il nome del linguaggio che implementa il metodo associato a questo frame dello stack.

 `pguidLanguage`

 [out] Restituisce il `GUID` del linguaggio. Per il [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] linguaggi, ad esempio, di seguito può essere restituiti:

- `guidVBScriptLang`

- `guidJScriptLang`

- `guidCPPLang`

- `guidVBLang`

- `guidSQLLang`

- `guidScriptLang`

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)