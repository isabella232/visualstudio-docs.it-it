---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
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
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "59001048"
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
 [in] Finestra padre  
  
 `dwID`  
 [in] ID per i visualizzatori personalizzati che supportano più di un tipo.  
  
 `pHostServices`  
 [in] Riservato. Sempre impostato su null.  
  
 `pDebugProperty`  
 [in] Interfaccia che può essere utilizzato per recuperare il valore da visualizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 La visualizzazione è "modal" in quanto questo metodo crea la finestra necessaria, visualizzare il valore, attende l'input e chiudere la finestra, tutti prima di restituire al chiamante. Ciò significa che il metodo deve gestire tutti gli aspetti della visualizzazione del valore della proprietà, dalla creazione di una finestra di output, in attesa di input dell'utente, all'eliminazione della finestra.  
  
 Per supportare la modifica del valore sul determinato [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dell'oggetto, è possibile utilizzare il [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) (metodo), ovvero se il valore può essere espresso sotto forma di stringa. In caso contrario, è necessario creare un'interfaccia personalizzata, ovvero esclusivo per l'analizzatore di espressioni l'implementazione di questa `DisplayValue` metodo, ovvero sullo stesso oggetto che implementa il `IDebugProperty3` interfaccia. Questa interfaccia personalizzata verrà forniti metodi per modificare i dati di una dimensione arbitraria o complessità.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
