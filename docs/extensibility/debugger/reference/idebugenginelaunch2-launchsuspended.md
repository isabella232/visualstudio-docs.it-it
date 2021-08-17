---
description: Questo metodo avvia un processo tramite il motore di debug (DE).
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c263b331ff33f0fbd146cb9eb9fdc29a92880b7a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079103"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Questo metodo avvia un processo tramite il motore di debug (DE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>Parametri
`pszMachine`\
[in] Nome del computer in cui avviare il processo. Usare un valore Null per specificare il computer locale.

`pPort`\
[in] Interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) che rappresenta la porta in cui verrà eseguito il programma.

`pszExe`\
[in] Nome dell'eseguibile da avviare.

`pszArgs`\
[in] Argomenti da passare all'eseguibile. Può essere un valore Null se non sono presenti argomenti.

`pszDir`\
[in] Nome della directory di lavoro utilizzata dall'eseguibile. Può essere un valore Null se non è necessaria alcuna directory di lavoro.

`bstrEnv`\
[in] Blocco di ambiente di stringhe con terminazione NULL, seguito da un carattere di terminazione NULL aggiuntivo.

`pszOptions`\
[in] Opzioni per l'eseguibile.

`dwLaunchFlags`\
[in] Specifica [l'LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) per una sessione.

`hStdInput`\
[in] Handle a un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdOutput`\
[in] Handle a un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdError`\
[in] Handle a un flusso di output degli errori alternativo. Può essere 0 se il reindirizzamento non è necessario.

`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che riceve gli eventi del debugger.

`ppDebugProcess`\
[out] Restituisce [l'oggetto IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) risultante che rappresenta il processo avviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 In [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] genere, avvia un programma usando il [metodo LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) e quindi collega il debugger al programma sospeso. Esistono tuttavia casi in cui il motore di debug potrebbe dover avviare un programma (ad esempio, se il motore di debug fa parte di un interprete e il programma di cui è in corso il debug è un linguaggio interpretato), nel qual caso usa il metodo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `IDebugEngineLaunch2::LaunchSuspended` .

 Il [metodo ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) viene chiamato per avviare il processo dopo che il processo è stato avviato correttamente in uno stato sospeso.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
