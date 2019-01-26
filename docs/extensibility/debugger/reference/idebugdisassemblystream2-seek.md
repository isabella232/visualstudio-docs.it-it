---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a2c3cf1a1a5ee17a3ecdb6ed6b097b3ff4dde18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976706"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Sposta il puntatore di lettura nel flusso di disassemblaggio di un determinato numero di istruzioni rispetto alla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
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
 [in] Un valore compreso il [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumerazione che specifica la posizione relativa per iniziare il processo di ricerca.  
  
 `pCodeContext`  
 [in] Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) che rappresenta il contesto di codice che l'operazione di ricerca è relativo alla. Questo parametro viene utilizzato solo se `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; in caso contrario, questo parametro viene ignorato e può essere un valore null.  
  
 `uCodeLocationId`  
 [in] L'identificatore percorso codice che l'operazione di ricerca è relativo alla. Questo parametro viene usato se `dwSeekStart`  =  `SEEK_START_CODELOCID`; in caso contrario, questo parametro viene ignorato e può essere impostato su 0. Vedere la sezione Osservazioni per il [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) metodo per una descrizione di un identificatore percorso codice.  
  
 `iInstructions`  
 [in] Il numero di istruzioni da spostare rispetto alla posizione specificata nel `dwSeekStart`. Questo valore può essere negativo per spostarsi all'indietro.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se è stata la posizione di ricerca a un punto successivo nell'elenco delle istruzioni disponibili. In caso contrario, verrà restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se la ricerca è stato in una posizione antecedente l'inizio dell'elenco, la posizione di lettura è impostata per la prima istruzione nell'elenco. Se il vedere è stato in una posizione dopo la fine dell'elenco, la posizione di lettura viene impostata all'ultima istruzione nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)