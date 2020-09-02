---
title: 'IDebugExpressionEvaluator:: setlocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57ddee6e1796159c505b67982f25d1ba09684561
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729467"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Questo metodo imposta il linguaggio da utilizzare per creare risultati stampabili.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametri
`wLangID`\
in Identificatore della lingua.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo può essere chiamato più volte durante il caricamento dell'analizzatore di espressioni (EE), quindi l'EE deve essere in grado di cambiare le lingue in tempo reale. EE usa questa impostazione locale per restituire i messaggi di errore e le stringhe nella lingua appropriata.

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
