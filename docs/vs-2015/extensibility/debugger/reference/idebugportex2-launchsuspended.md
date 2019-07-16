---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188450"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Avvia un file eseguibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
