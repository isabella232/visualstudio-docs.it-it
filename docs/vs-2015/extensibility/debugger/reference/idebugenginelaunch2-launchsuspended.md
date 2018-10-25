---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbbebe758a73a4480a798e988535c907a33bae13
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922646"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo avvia un processo mediante il motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametri  
 `pszMachine`  
 [in] Il nome del computer in cui si desidera avviare il processo. Utilizzare un valore null per specificare il computer locale.  
  
 `pPort`  
 [in] Il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia che rappresenta la porta che il programma verrà eseguito in.  
  
 `pszExe`  
 [in] Il nome del file eseguibile da avviare.  
  
 `pszArgs`  
 [in] Gli argomenti da passare all'eseguibile. Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 [in] Il nome della directory di lavoro usato dall'eseguibile. Può essere un valore null se non è necessaria alcuna directory di lavoro.  
  
 `bstrEnv`  
 [in] Blocco di ambiente di stringhe con terminazione NULL, seguita da un terminatore NULL aggiuntivo.  
  
 `pszOptions`  
 [in] Le opzioni per il file eseguibile.  
  
 `dwLaunchFlags`  
 [in] Specifica la [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) per una sessione.  
  
 `hStdInput`  
 [in] Handle per un flusso di input alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdOutput`  
 [in] Handle per un flusso di output alternativi. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdError`  
 [in] Handle per un flusso di output di errore alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `pCallback`  
 [in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto che riceve gli eventi del debugger.  
  
 `ppDebugProcess`  
 [out] Restituisce l'oggetto risultante [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) oggetto che rappresenta il processo avviato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] avvia un programma tramite il [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) (metodo) e quindi collega il debugger al programma sospesi. Tuttavia, esistono circostanze in cui potrebbe essere necessario avviare un programma (ad esempio, se il motore di debug fa parte di un interprete e il programma sottoposto a debug è un linguaggio interpretato), nel qual caso il motore di debug [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] utilizza il `IDebugEngineLaunch2::LaunchSuspended` (metodo) .  
  
 Il [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) viene chiamato per avviare il processo dopo il processo è stato avviato in uno stato sospeso.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

