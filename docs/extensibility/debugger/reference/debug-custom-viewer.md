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
ms.openlocfilehash: 683164a2a3c6e6e63d4a783d55ea481d3eb8547f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065098"
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
ID per distinguere più visualizzatori o visualizzatori implementati da un `GUID` oggetto .

`bstrMenuName`\
Testo che verrà visualizzato nel menu a discesa.

`bstrDescription`\
Descrizione del visualizzatore personalizzato o del visualizzatore di tipi (se non usato deve essere un valore Null).

`guidLang`\
Linguaggio dell'analizzatore di espressioni fornito.

`guidVendor`\
Fornitore dell'analizzatore di espressioni fornito.

`bstrMetric`\
Metrica in cui è archiviato il visualizzatore personalizzato o il `CLSID` visualizzatore di tipi.

## <a name="remarks"></a>Commenti
Un elenco di questa struttura viene restituito da una chiamata al [metodo GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (e, per estensione, al [metodo GetCustomViewerList).](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
