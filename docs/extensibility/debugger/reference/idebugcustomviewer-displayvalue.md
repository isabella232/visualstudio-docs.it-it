---
title: Proprietà IDebugCustomViewer::DisplayValue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732444"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Questo metodo viene chiamato per visualizzare il valore specificato.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="parameters"></a>Parametri
`hwnd`\
[in] Finestra Padre

`dwID`\
[in] ID per visualizzatori personalizzati che supportano più di un tipo.

`pHostServices`\
[in] Riservato. Sempre impostato su null.

`pDebugProperty`\
[in] Interfaccia che può essere utilizzata per recuperare il valore da visualizzare.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso contrario restituisce il codice di errore.

## <a name="remarks"></a>Osservazioni
 La visualizzazione è "modale" in quanto questo metodo creerà la finestra necessaria, visualizzerà il valore, attenderà l'input e chiude la finestra, il tutto prima di tornare al chiamante. Ciò significa che il metodo deve gestire tutti gli aspetti della visualizzazione del valore della proprietà, dalla creazione di una finestra per l'output, all'attesa dell'input dell'utente, all'eliminazione della finestra.

 Per supportare la modifica del valore nell'oggetto [Specificato IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) oggetto, è possibile utilizzare il [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) metodo, se il valore può essere espresso come stringa. In caso contrario, è necessario creare un'interfaccia personalizzata, in esclusiva per l'analizzatore di espressioni che implementa questo `DisplayValue` metodo, sullo stesso oggetto che implementa l'interfaccia. `IDebugProperty3` Questa interfaccia personalizzata fornirebita metodi per modificare i dati di una dimensione o complessità arbitraria.

## <a name="see-also"></a>Vedere anche
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
