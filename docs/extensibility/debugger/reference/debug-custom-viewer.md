---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe17c8747d5c678c14561a918ddd9d62bd658841
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315833"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Struttura che identifica un visualizzatore personalizzato o digitare Visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Membri
dwID  
Un ID per distinguere più visualizzatori o visualizzatori implementati da una `GUID`.

bstrMenuName  
Il testo che verrà visualizzato nel menu a discesa.

bstrDescription  
Descrizione del visualizzatore personalizzato o Visualizzatore di tipi (deve essere un valore null se non utilizzato).

guidLang  
Lingua dell'analizzatore di espressioni che fornisce.

guidVendor  
Fornitore dell'analizzatore di espressioni che fornisce.

bstrMetric  
Metrica in base alle quali il visualizzatore personalizzato o Visualizzatore di tipi `CLSID` viene archiviato.

## <a name="remarks"></a>Note
Viene restituito da una chiamata a un elenco di questa struttura i [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo (e, di conseguenza, il [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) (metodo)).

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)  
[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
