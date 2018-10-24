---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a16241e406ea89b33c417bd873949979c3f6e82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882314"
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
  
#### <a name="parameters"></a>Parametri  
 `pszExe`  
 [in] Il nome del file eseguibile da avviare. Può trattarsi di un percorso completo o relativo alla directory di lavoro specificata nella `pszDir` parametro.  
  
 `pszArgs`  
 [in] Gli argomenti da passare all'eseguibile. Può essere un valore null se non sono presenti argomenti.  
  
 `pszDir`  
 [in] Il nome della directory di lavoro usato dall'eseguibile. Può essere un valore null se non è necessaria alcuna directory di lavoro.  
  
 `bstrEnv`  
 [in] Blocco di ambiente di stringhe con terminazione null, seguita da un terminatore NULL aggiuntivo.  
  
 `hStdInput`  
 [in] Handle per un flusso di input alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdOutput`  
 [in] Handle per un flusso di output alternativi. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `hStdError`  
 [in] Handle per un flusso di output di errore alternativo. Può essere 0 se il reindirizzamento non è obbligatorio.  
  
 `ppPortProcess`  
 [out] Restituisce un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) oggetto che rappresenta il processo avviato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere avviato il processo in modo che l'it è sospesa e non in esecuzione alcun codice. Il [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) metodo viene chiamato per riprendere il processo.  
  
 Un programma può anche essere avviato da un motore di debug. Per informazioni dettagliate, vedere [avviando un programma](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Avvio di un programma](../../../extensibility/debugger/launching-a-program.md)