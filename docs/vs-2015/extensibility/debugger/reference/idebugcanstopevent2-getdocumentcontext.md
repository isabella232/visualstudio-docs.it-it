---
title: 'IDebugCanStopEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241e5cff6aee533a2a5899116acef3d928985d1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191168"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il contesto del documento che descrive la posizione di questo evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppDocCxt`  
 out Restituisce l'interfaccia [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) che rappresenta una posizione in un documento del file di origine corrispondente al percorso del codice corrente.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 In genere, il contesto del documento può essere considerato come una posizione in un file di origine.  
  
 Per ottenere il contesto del codice, che è orientato alle istruzioni del codice, chiamare il metodo [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
