---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6203b12defbe70d3807508953d85f39ff725a746
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693518"
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

#### <a name="parameters"></a>Parametri
 `guidLaunchingEngine`

 [in] Il `GUID` di un CRI che deve essere utilizzato per avviare programmi (e si presuppone per aggiungere nodi di un proprio programma).

 `rgguidSpecificEngines`

 [in] Matrice di `GUID`s di DEs per il programma che verranno aggiunti i nodi.

 `celtSpecificEngines`

 [in] I numerosi `GUID`s nel `rgguidSpecificEngines` matrice.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
- [I nodi di programma](../../../extensibility/debugger/program-nodes.md) verranno aggiunti per ogni Germania elencati nella `rgguidSpecificEngines`, escluso il motore che esegue l'applicazione (come specificato in `guidLaunchingEngine`), che vengono utilizzati per aggiungere il proprio nodo programma quando avvia un programma.

## <a name="see-also"></a>Vedere anche
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
- [Nodi di programma](../../../extensibility/debugger/program-nodes.md)