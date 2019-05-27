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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ef0ce265bc63ce9a00fd748c50a338d52294557
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211692"
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

## <a name="parameters"></a>Parametri
`pbstrEngine`\
[out] Restituisce il nome della DE esecuzione del programma (C++-specifici: può trattarsi di un puntatore null, che indica che il chiamante non è interessato il nome il modulo di gestione).

`pguidEngine`\
[out] Restituisce l'identificatore univoco globale della DE esecuzione del programma (C++-specifici: può trattarsi di un puntatore null, che indica che il chiamante non è interessato il GUID del motore).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)