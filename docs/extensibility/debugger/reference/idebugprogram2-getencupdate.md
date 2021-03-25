---
description: Questo metodo ottiene l'aggiornamento di modifica e continuazione (ENC) per questo programma.
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d6b60c8b17a8db1420222a7242164ce1c0eedd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075926"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Questo metodo ottiene l'aggiornamento di modifica e continuazione (ENC) per questo programma. Un modulo di debug personalizzato restituisce sempre `E_NOTIMPL`.

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
out Restituisce un'interfaccia interna che può essere utilizzata per aggiornare il programma.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

> [!NOTE]
> Un motore di debug personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
