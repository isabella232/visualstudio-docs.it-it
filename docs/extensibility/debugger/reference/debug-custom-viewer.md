---
title: DEBUG_CUSTOM_VIEWER . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737537"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Struttura che identifica un visualizzatore personalizzato o un visualizzatore di tipo.

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
`dwID`\
UN ID per differenziare più visualizzatori o visualizzatori implementati da un file `GUID`.

`bstrMenuName`\
Il testo che verrà visualizzato nel menu a discesa.

`bstrDescription`\
Una descrizione del visualizzatore personalizzato o del visualizzatore di tipo (deve essere un valore null se non viene utilizzato).

`guidLang`\
Linguaggio dell'analizzatore di espressioni fornito.

`guidVendor`\
Fornitore dell'analizzatore di espressioni fornito.

`bstrMetric`\
Metrica in cui è archiviato il visualizzatore personalizzato o il visualizzatore `CLSID` di tipo.

## <a name="remarks"></a>Osservazioni
Un elenco di questa struttura viene restituito da una chiamata al [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) metodo (e, per estensione, il [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metodo).

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
