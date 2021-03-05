---
description: Ottiene il nome della sessione che esegue il debug del processo.
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d83a9d5f89ea06744454b790d988f1881c193b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142544"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ottiene il nome della sessione che esegue il debug del processo. Un IDE può visualizzare queste informazioni a un utente che esegue il debug di un determinato processo su un computer specifico.

> [!NOTE]
> Questo metodo è deprecato e la relativa implementazione deve sempre restituire `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parametri
`pbstrSessionName`\

## <a name="return-value"></a>Valore restituito
 Questo metodo deve sempre restituire `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
