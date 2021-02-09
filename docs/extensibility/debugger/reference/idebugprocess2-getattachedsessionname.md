---
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
ms.openlocfilehash: a4692fdbc08655553a829c0f44037221f2e8b410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907867"
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
