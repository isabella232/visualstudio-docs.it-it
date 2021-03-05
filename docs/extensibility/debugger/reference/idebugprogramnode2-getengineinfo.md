---
description: Ottiene il nome e l'identificatore del motore di debug (DE) che esegue un programma.
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d09ec8b7503047a9dcece353c859c607289a005b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145989"
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
out Restituisce il nome del DE che esegue il programma (specifico di C++: può trattarsi di un puntatore null che indica che il chiamante non è interessato al nome del motore).

`pguidEngine`\
out Restituisce l'identificatore univoco globale del DE che esegue il programma (specifico di C++: può essere un puntatore null che indica che il chiamante non è interessato al GUID del motore).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
