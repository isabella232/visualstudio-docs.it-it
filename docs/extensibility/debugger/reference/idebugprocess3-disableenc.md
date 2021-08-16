---
description: Questo metodo disabilita in modo esplicito Modifica e continuazione in questo processo (e in tutti i programmi in esso contenuti).
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 429cacbc4ef87224459493b0815d9e5dcff7fac3f61ca510d334501226a08eef
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121276737"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Questo metodo disabilita in modo esplicito Modifica e continuazione in questo processo (e in tutti i programmi in esso contenuti). Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametri
`reason`\
[in] Valore [dell'enumerazione EncUnavailableReason.](../../../extensibility/debugger/reference/encunavailablereason.md)

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

> [!NOTE]
> Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="remarks"></a>Commenti
 Dopo aver disabilitato Modifica e continuazione per un processo, è possibile ri enabledarlo solo riavviando il processo.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
