---
title: IDebugEngineLaunch2::LaunchSuspended Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730552"
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
[in] Nome della macchina in cui avviare il processo. Utilizzare un valore null per specificare il computer locale.

`pPort`\
[in] Il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia che rappresenta la porta in cui verrà eseguito il programma.

`pszExe`\
[in] Nome dell'eseguibile da avviare.

`pszArgs`\
[in] Argomenti da passare all'eseguibile. Può essere un valore null se non sono presenti argomenti.

`pszDir`\
[in] Nome della directory di lavoro utilizzata dall'eseguibile. Può essere un valore null se non è richiesta alcuna directory di lavoro.

`bstrEnv`\
[in] Blocco di ambiente di stringhe con terminazione NULL, seguito da un terminatore NULL aggiuntivo.

`pszOptions`\
[in] Opzioni per l'eseguibile.

`dwLaunchFlags`\
[in] Specifica il [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) per una sessione.

`hStdInput`\
[in] Handle a un flusso di input alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdOutput`\
[in] Handle per un flusso di output alternativo. Può essere 0 se il reindirizzamento non è necessario.

`hStdError`\
[in] Handle per un flusso di output degli errori alternativo. Può essere 0 se il reindirizzamento non è necessario.

`pCallback`\
[in] Oggetto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) che riceve gli eventi del debugger.

`ppDebugProcess`\
[fuori] Restituisce l'oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) risultante che rappresenta il processo avviato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 In [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] genere, avvia un programma utilizzando il [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) metodo e quindi collega il debugger al programma sospeso. Tuttavia, in alcune circostanze il motore di debug potrebbe essere necessario avviare un programma (ad esempio, se il motore di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debug `IDebugEngineLaunch2::LaunchSuspended` fa parte di un interprete e il programma in fase di debug è un linguaggio interpretato), nel qual caso utilizza il metodo .

 Il [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) metodo viene chiamato per avviare il processo dopo che il processo è stato avviato correttamente in uno stato sospeso.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
