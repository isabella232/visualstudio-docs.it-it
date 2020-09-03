---
title: 'IDebugDisassemblyStream2:: Seek | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d774cc0bf6bca1278423249960bbc5233aa6ad37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203020"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sposta il puntatore di lettura nel flusso di disassembly per un determinato numero di istruzioni rispetto a una posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwSeekStart`  
 in Valore dell'enumerazione [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) che specifica la posizione relativa per avviare il processo di ricerca.  
  
 `pCodeContext`  
 in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto del codice a cui è relativa l'operazione di ricerca. Questo parametro viene utilizzato solo se `dwSeekStart`  =  `SEEK_START_CODECONTEXT` ; in caso contrario, questo parametro viene ignorato e può essere un valore null.  
  
 `uCodeLocationId`  
 in Identificatore del percorso del codice a cui è relativa l'operazione di ricerca. Questo parametro viene utilizzato se `dwSeekStart`  =  `SEEK_START_CODELOCID` ; in caso contrario, questo parametro viene ignorato e può essere impostato su 0. Per una descrizione dell'identificatore di una posizione del codice, vedere la sezione Osservazioni per il metodo [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .  
  
 `iInstructions`  
 in Numero di istruzioni da spostare rispetto alla posizione specificata in `dwSeekStart` . Questo valore può essere negativo per spostarsi all'indietro.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se la posizione di ricerca è a un punto successivo all'elenco di istruzioni disponibili. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Osservazioni  
 Se la ricerca è stata posizionata prima dell'inizio dell'elenco, la posizione di lettura viene impostata sulla prima istruzione dell'elenco. Se la posizione di visualizzazione è successiva alla fine dell'elenco, la posizione di lettura viene impostata sull'ultima istruzione nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
