---
title: 'IDebugDisassemblyStream2:: GetCodeLocationId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebb2280f814985e2352413921a00268d96761b7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196234"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce un identificatore di posizione del codice per un particolare contesto di codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCodeContext`  
 in Oggetto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) da convertire in un identificatore.  
  
 `puCodeLocationId`  
 out Restituisce l'identificatore della posizione del codice. Vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Restituisce `E_CODE_CONTEXT_OUT_OF_SCOPE` se il contesto del codice è valido ma esterno all'ambito.  
  
## <a name="remarks"></a>Osservazioni  
 L'identificatore del percorso del codice è specifico del motore di debug (DE) che supporta il disassembly. Questo identificatore di percorso viene utilizzato internamente da DE per tenere traccia delle posizioni nel codice ed è in genere un indirizzo o un offset di qualche tipo. L'unico requisito è che se il contesto del codice di una posizione è inferiore al contesto del codice di un'altra posizione, l'identificatore del percorso di codice corrispondente del primo contesto di codice deve essere minore di quello del secondo contesto di codice.  
  
 Per recuperare il contesto del codice di un identificatore del percorso di codice, chiamare il metodo [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)
