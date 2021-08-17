---
description: Avvia un file eseguibile.
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c6db6cc7f67cc8cb4106215d33eb791c551a66b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030282"
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
[in] Nome dell'eseguibile da avviare. Può trattarsi di un percorso completo o relativo alla directory di lavoro specificata nel `pszDir` parametro .

`pszArgs`\
[in] Argomenti da passare all'eseguibile. Può essere un valore Null se non sono presenti argomenti.

`pszDir`\
[in] Nome della directory di lavoro utilizzata dall'eseguibile. Può essere un valore Null se non è necessaria alcuna directory di lavoro.

`bstrEnv`\
[in] Blocco di ambiente di stringhe con terminazione Null, seguito da un carattere di terminazione NULL aggiuntivo.

`hStdInput`\
[in] Handle a un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdOutput`\
[in] Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdError`\
[in] Handle a un flusso di output degli errori alternativo. Può essere 0 se il reindirizzamento non è necessario.

`ppPortProcess`\
[out] Restituisce un [oggetto IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) che rappresenta il processo avviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo deve avviare il processo in modo che sia sospeso e non ese in esecuzione alcun codice. Il [metodo ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) viene chiamato per riprendere il processo.

 Un programma può essere avviato anche da un motore di debug. Per informazioni dettagliate, vedere [Avvio di un programma.](../../../extensibility/debugger/launching-a-program.md)

## <a name="see-also"></a>Vedi anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md)
