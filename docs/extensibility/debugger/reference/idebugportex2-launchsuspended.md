---
title: Proprietà IDebugPortEx2::LaunchSuspended . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725107"
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
[in] Nome dell'eseguibile da avviare. Può trattarsi di un percorso completo o `pszDir` relativo alla directory di lavoro specificata nel parametro .

`pszArgs`\
[in] Argomenti da passare all'eseguibile. Può essere un valore null se non sono presenti argomenti.

`pszDir`\
[in] Nome della directory di lavoro utilizzata dall'eseguibile. Può essere un valore null se non è richiesta alcuna directory di lavoro.

`bstrEnv`\
[in] Blocco di ambiente di stringhe con terminazione null, seguito da un carattere di terminazione NULL aggiuntivo.

`hStdInput`\
[in] Handle a un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdOutput`\
[in] Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdError`\
[in] Handle per un flusso di output degli errori alternativo. Può essere 0 se il reindirizzamento non è necessario.

`ppPortProcess`\
[fuori] Restituisce un oggetto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) che rappresenta il processo avviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo deve avviare il processo in modo che venga sospeso e non eseguire alcun codice. Il [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) metodo viene chiamato per riprendere il processo.

 Un programma può anche essere avviato da un motore di debug. Per informazioni dettagliate, vedere [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Vedere anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md)
