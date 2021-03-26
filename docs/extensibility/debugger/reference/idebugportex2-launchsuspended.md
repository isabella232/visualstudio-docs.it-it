---
description: Avvia un file eseguibile.
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fdffb6f87285e9f33d6abaf864b4d45345a304ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072494"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Avvia un file eseguibile.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parametri
`pszExe`\
in Nome del file eseguibile da avviare. Può trattarsi di un percorso completo o relativo alla directory di lavoro specificata nel `pszDir` parametro.

`pszArgs`\
in Argomenti da passare al file eseguibile. Può essere un valore null se non sono presenti argomenti.

`pszDir`\
in Nome della directory di lavoro utilizzata dal file eseguibile. Può essere un valore null se non è richiesta alcuna directory di lavoro.

`bstrEnv`\
in Blocco dell'ambiente di stringhe con terminazione null, seguito da un carattere di terminazione NULL aggiuntivo.

`hStdInput`\
in Handle per un flusso di input alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.

`hStdOutput`\
in Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.

`hStdError`\
in Handle per un flusso di output degli errori alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.

`ppPortProcess`\
out Restituisce un oggetto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) che rappresenta il processo avviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo deve avviare il processo in modo che venga sospeso e non esegua alcun codice. Per riprendere il processo, viene chiamato il metodo [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) .

 Un programma può essere avviato anche da un motore di debug. Per informazioni dettagliate, vedere [avvio di un programma](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Vedi anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md)
