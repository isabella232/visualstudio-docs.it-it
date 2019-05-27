---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 363018d13cfeee1691881f4d8b814cdd0b2dfa35
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212345"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Questo metodo ottiene l'aggiornamento di modifica e Continuazione per il programma. Un motore di debug personalizzato restituisce sempre `E_NOTIMPL`.

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
[out] Restituisce un'interfaccia interna che può essere utilizzata per aggiornare il programma.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

> [!NOTE]
> Un motore di debug personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)