---
description: Struttura che identifica un visualizzatore personalizzato o un visualizzatore di tipi.
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e2aa32e5bf04e4f5c931ec3e8de3d156f7c8bcebb993749d8e348075523a7be4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390359"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Struttura che identifica un visualizzatore personalizzato o un visualizzatore di tipi.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Members
`dwID`\
ID per distinguere più visualizzatori o visualizzatori implementati da un oggetto `GUID` .

`bstrMenuName`\
Testo che verrà visualizzato nel menu a discesa.

`bstrDescription`\
Descrizione del visualizzatore personalizzato o del visualizzatore di tipi (deve essere un valore Null se non viene usato).

`guidLang`\
Linguaggio dell'analizzatore di espressioni fornito.

`guidVendor`\
Fornitore dell'analizzatore di espressioni fornito.

`bstrMetric`\
Metrica in cui è archiviato il visualizzatore personalizzato o il `CLSID` visualizzatore di tipi.

## <a name="remarks"></a>Commenti
Un elenco di questa struttura viene restituito da una chiamata al metodo [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (e, per estensione, dal [metodo GetCustomViewerList).](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
