---
description: Ottiene la lingua associata a questo stack frame.
title: Interfaccia IDebugStackFrame2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7b87cc242a1d9abeaebdfe768bb101dead6d134
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063733"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Ottiene la lingua associata a questo stack frame.

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

## <a name="parameters"></a>Parametri

`pbstrLanguage`\
[out] Restituisce il nome del linguaggio che implementa il metodo associato a questo stack frame.

`pguidLanguage`\
[out] Restituisce `GUID` l'oggetto della lingua. Per le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] lingue, ad esempio, è possibile restituire quanto segue:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Valore restituito

 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
