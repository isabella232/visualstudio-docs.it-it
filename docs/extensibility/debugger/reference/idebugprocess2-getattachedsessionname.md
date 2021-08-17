---
description: Ottiene il nome della sessione che esegue il debug di questo processo.
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 65fa413d5538d0290afc85cea8d42f389098e5082cf064a57d09a51cc2c3b43e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416326"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Ottiene il nome della sessione che esegue il debug di questo processo. Un IDE può visualizzare queste informazioni a un utente che esegue il debug di un processo specifico in un computer specifico.

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
