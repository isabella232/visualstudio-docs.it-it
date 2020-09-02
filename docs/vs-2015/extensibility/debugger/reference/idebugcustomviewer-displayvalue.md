---
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bda4c60e9164ae195c0e3ba49893b1a818c66f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421372"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo viene chiamato per visualizzare il valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hwnd`  
 in Finestra padre  
  
 `dwID`  
 in ID per i visualizzatori personalizzati che supportano più di un tipo.  
  
 `pHostServices`  
 [in] Riservato. Sempre impostato su null.  
  
 `pDebugProperty`  
 in Interfaccia che può essere utilizzata per recuperare il valore da visualizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 La visualizzazione è "modale" poiché questo metodo creerà la finestra necessaria, visualizzerà il valore, attenderà l'input e chiuderà la finestra, prima di tornare al chiamante. Questo significa che il metodo deve gestire tutti gli aspetti della visualizzazione del valore della proprietà, dalla creazione di una finestra per l'output, all'attesa dell'input dell'utente, per eliminare definitivamente la finestra.  
  
 Per supportare la modifica del valore sull'oggetto [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) specificato, è possibile usare il metodo [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) , se il valore può essere espresso come stringa. In caso contrario, è necessario creare un'interfaccia personalizzata, esclusiva dell'analizzatore di espressioni che implementa questo `DisplayValue` metodo, sullo stesso oggetto che implementa l' `IDebugProperty3` interfaccia. Questa interfaccia personalizzata fornirebbe metodi per la modifica dei dati di una dimensione o complessità arbitraria.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
