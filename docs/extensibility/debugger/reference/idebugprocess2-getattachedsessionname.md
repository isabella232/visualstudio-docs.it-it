---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84a0969eb93fc2e95449364521662c27bf6f750d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202647"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ottiene il nome della sessione che sta eseguendo il debug questo processo. Un IDE per visualizzare queste informazioni a un utente che il debug di un processo specifico in un computer specifico.

> [!NOTE]
> Questo metodo è deprecato e la relativa implementazione deve sempre restituire `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametri
`pbstrSessionName`\

## <a name="return-value"></a>Valore restituito
 Questo metodo deve sempre restituire `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)