---
description: Questo metodo viene chiamato per visualizzare il valore specificato.
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3ff715cadd6499d74d3704faa9ad0e078d0838ee931b4fc6b68c4588fb45cc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377821"
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
[in] Finestra padre

`dwID`\
[in] ID per i visualizzatori personalizzati che supportano più di un tipo.

`pHostServices`\
[in] Riservato. Sempre impostato su Null.

`pDebugProperty`\
[in] Interfaccia che può essere utilizzata per recuperare il valore da visualizzare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 La visualizzazione è "modale" in quanto questo metodo crea la finestra necessaria, visualizza il valore, attende l'input e chiude la finestra, il tutto prima di tornare al chiamante. Ciò significa che il metodo deve gestire tutti gli aspetti della visualizzazione del valore della proprietà, dalla creazione di una finestra per l'output, all'attesa dell'input dell'utente fino all'eliminazione della finestra.

 Per supportare la modifica del valore nell'oggetto [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) specificato, è possibile usare il [metodo SetValueAsStringWithError,](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) se il valore può essere espresso come stringa. In caso contrario, è necessario creare un'interfaccia personalizzata, esclusiva dell'analizzatore di espressioni che implementa questo metodo, nello stesso oggetto `DisplayValue` che implementa `IDebugProperty3` l'interfaccia . Questa interfaccia personalizzata fornisce metodi per la modifica dei dati di dimensioni arbitrarie o complessità.

## <a name="see-also"></a>Vedi anche
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
