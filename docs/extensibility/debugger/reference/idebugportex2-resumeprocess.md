---
title: IDebugPortEx2::ResumeProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::ResumeProcess
helpviewer_keywords:
- IDebugPortEx2::ResumeProcess
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7549ffc7375611d22e0ced603104e6a05d964b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708849"
---
# <a name="idebugportex2resumeprocess"></a>IDebugPortEx2::ResumeProcess
Riprende l'esecuzione di un processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ResumeProcess( 
   IDebugProcess2* pPortProcess
);
```

```cpp
int ResumeProcess( 
   IDebugProcess2 pPortProcess
);
```

#### <a name="parameters"></a>Parametri
 `pPortProcess`

 [in] Un' [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo di essere ripreso.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)