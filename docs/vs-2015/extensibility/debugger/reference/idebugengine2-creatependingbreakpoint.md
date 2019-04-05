---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954537"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un punto di interruzione in sospeso nel motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pBPRequest`  
 [in] Un' [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) che descrive il punto di interruzione in sospeso da creare.  
  
 `ppPendingBP`  
 [out] Restituisce un [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) oggetto che rappresenta il punto di interruzione in sospeso.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Restituisce in genere `E_FAIL` se il `pBPRequest` parametro non corrisponde a qualsiasi linguaggio supportato da DE se il `pBPRequest` parametro non è valida o incompleta.  
  
## <a name="remarks"></a>Note  
 Un punto di interruzione in sospeso è essenzialmente una raccolta di tutte le informazioni necessarie per associare un punto di interruzione al codice. Il punto di interruzione in sospeso restituito da questo metodo non è associato al codice finché il [associare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) viene chiamato il metodo.  
  
 Per ogni punto di interruzione, l'utente imposta gestore di sessione di debug (SDM) chiama questo metodo in ogni DE collegati. È compito DE per verificare che il punto di interruzione sia valido per i programmi in esecuzione in tale DE.  
  
 Quando l'utente imposta un punto di interruzione su una riga di codice, la Germania è gratuito associare il punto di interruzione di riga più vicina del documento che corrisponde a questo codice. Questo rende possibile l'utente può impostare un punto di interruzione sulla prima riga di un'istruzione su più righe, ma la si associa l'ultima riga (in cui tutto il codice con attribuito nelle informazioni di debug).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CProgram` oggetto. Implementazione di DE del `IDebugEngine2::CreatePendingBreakpoint` potrebbe quindi inoltrare tutte le chiamate a questa implementazione del metodo in ogni programma.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Eseguire l'associazione](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
