---
description: Questo metodo aggiunge un nodo di programma per ogni motore di debug (DE) specificato.
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3a4c6446c2106d79dd14fc0378fc848eac3df18
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159991"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Questo metodo aggiunge un nodo di programma per ogni motore di debug (DE) specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT AddImplicitProgramNodes(
   REFGUID guidLaunchingEngine,
   GUID*   rgguidSpecificEngines,
   DWORD   celtSpecificEngines
);
```

```csharp
int AddImplicitProgramNodes(
   ref Guid guidLaunchingEngine,
   Guid[]   rgguidSpecificEngines,
   uint     celtSpecificEngines
);
```

## <a name="parameters"></a>Parametri
`guidLaunchingEngine`\
in `GUID` Di un de da usare per avviare i programmi (si presuppone che aggiunga i propri nodi del programma).

`rgguidSpecificEngines`\
in Matrice di `GUID` des per cui verranno aggiunti i nodi del programma.

`celtSpecificEngines`\
in Numero di `GUID` s nella `rgguidSpecificEngines` matrice.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
- I [nodi del programma](../../../extensibility/debugger/program-nodes.md) verranno aggiunti per ogni de elencato in, `rgguidSpecificEngines` escluso il motore di avvio (come indicato in `guidLaunchingEngine` ), che si presuppone aggiungere il proprio nodo di programma all'avvio di un programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nodi di programma](../../../extensibility/debugger/program-nodes.md)
