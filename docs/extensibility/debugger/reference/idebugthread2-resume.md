---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4997b8c711a67a3bb45529627e81e70b786acf00
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915509"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Riprende l'esecuzione di un thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

#### <a name="parameters"></a>Parametri
 `pdwSuspendCount`

 [out] Restituisce il conteggio di sospensione al termine dell'operazione di ripresa.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a raggiungere 0 a quel punto, in realtà ripresa l'esecuzione. Questo conteggio di sospensione viene visualizzato nei **thread** finestra di debug.

 Per ogni chiamata a questo metodo, deve esistere una chiamata precedente al [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) (metodo). Il conteggio di suspend determina quante volte il `IDebugThread2::Suspend` metodo è stato chiamato fino a questo momento.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)