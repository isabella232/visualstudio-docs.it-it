---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421eea42c169f586657998e5d4cd57c4c797b71e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916904"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
Ottiene il nome e l'identificatore del motore di debug (DE) che esegue un programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

#### <a name="parameters"></a>Parametri
 `pbstrEngine`

 [out] Restituisce il nome della DE esecuzione del programma (C++-specifici: può trattarsi di un puntatore null, che indica che il chiamante non è interessato il nome il modulo di gestione).

 `pguidEngine`

 [out] Restituisce l'identificatore univoco globale della DE esecuzione del programma (C++-specifici: può trattarsi di un puntatore null, che indica che il chiamante non è interessato il GUID del motore).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)