---
description: Questo metodo ottiene l'aggiornamento ENC (Edit and Continue) per questo programma.
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d124a1cd00f999c41bfc5259183658aada84696
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132756"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Questo metodo ottiene l'aggiornamento ENC (Edit and Continue) per questo programma. Un modulo di debug personalizzato restituisce sempre `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parametri
`ppUpdate`\
[out] Restituisce un'interfaccia interna che può essere utilizzata per aggiornare questo programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un motore di debug personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
