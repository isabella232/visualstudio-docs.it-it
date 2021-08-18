---
description: Ottiene l'identificatore del processo di sistema per il processo che ospita il programma.
title: Interfaccia IDebugProgramNode2::GetHostPid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostPid
helpviewer_keywords:
- IDebugProgramNode2::GetHostPid
ms.assetid: e65b4b15-46d8-4ca7-9456-2b4c078f7cf9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3458ab1f9e7e6049736c85189ca437406401575b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050585"
---
# <a name="idebugprogramnode2gethostpid"></a>IDebugProgramNode2::GetHostPid
Ottiene l'identificatore del processo di sistema per il processo che ospita il programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostPid ( 
   AD_PROCESS_ID * pdwHostPid
);
```

```csharp
int GetHostPid ( 
   out AD_PROCESS_ID pdwHostPid
);
```

## <a name="parameters"></a>Parametri
`pdwHostPid`\
[out] Restituisce l'identificatore del processo di sistema per il processo di hosting.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto `CProgram` semplice che implementa [l'interfaccia IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md)

```cpp
HRESULT CProgram::GetHostPid(AD_PROCESS_ID* pdwHostPid) {
   // Check for valid argument.
   if (pdwHostPid == NULL)
     return E_INVALIDARG;

   // Get the process identifier of the calling process.
   pdwHostPid->ProcessIdType = AD_PROCESS_ID_SYSTEM;
   pdwHostPid->ProcessId.dwProcessId = GetCurrentProcessId();
   return S_OK;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
