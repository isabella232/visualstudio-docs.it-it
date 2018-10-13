---
title: IDebugParsedExpression::EvaluateSync | Microsoft Docs
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
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01c75f47d2014ab833e7d213bdd871fbb8c4f1a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236821"
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo valuta l'espressione analizzata e facoltativamente esegue il cast del risultato a un altro tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwEvalFlags`  
 [in] Una combinazione di [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) costanti che controllano il modo in cui l'espressione deve essere valutata.  
  
 `dwTimeout`  
 [in] Specifica il tempo massimo, espresso in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per un'attesa indefinita.  
  
 `pSymbolProvider`  
 [in] Il provider di simboli, espresso come un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) interfaccia.  
  
 `pAddress`  
 [in] Il percorso di esecuzione corrente all'interno di un metodo, espresso come un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interfaccia.  
  
 `pBinder`  
 [in] Lo strumento di associazione, espresso come un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaccia.  
  
 `bstrResultType`  
 [in] Il risultato dovrebbe essere eseguire il cast. Questo argomento può essere un valore null.  
  
 `ppResult`  
 [out] Restituisce il [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaccia che rappresenta i risultati della valutazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Contesto di valutazione dell'espressione è dato dai `pAddress`, che rende possibile determinare il metodo contenitore e dell'ambito di utilizzo del linguaggio delle regole per determinare il valore dei simboli nell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)

