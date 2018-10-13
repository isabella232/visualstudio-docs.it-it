---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
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
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f6bbb0077fcc8dd8d151b995a9c416113e1b5ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243438"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo crea un servizio del visualizzatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `binder`  
 [in] Il [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) l'oggetto passato al [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] Il [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) l'oggetto passato al `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] Il [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) l'oggetto passato al `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Oggetto che implementa il [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interfaccia (fornito dall'analizzatore di espressioni).  
  
 `ppService`  
 [out] Il servizio creato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il `binder`, `pSymProv`, e `pAddress` tutti i parametri sono stati passati al `IDebugParsedExpression::EvaluateSync` (metodo). `CreateVisualizerService` deve essere chiamato solo da `IDebugParsedExpression::EvaluateSync` come parte del supporto di un analizzatore di espressioni per i visualizzatori di tipi.  
  
## <a name="see-also"></a>Vedere anche  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

