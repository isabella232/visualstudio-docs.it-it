---
description: Enumera i valori validi che rappresentano i tipi di informazioni da ottenere da un oggetto IDebugField e visualizzarli all'utente.
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11d6cd9390b115b583df5d83db102af0253bf13384d7e612af65edfc6536ccd6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378029"
---
# <a name="displaykind"></a>DisplayKind
Enumera i valori validi che rappresentano i tipi di informazioni da ottenere da un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e visualizzarli all'utente.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
typedef DWORD DisplayKind;
```

```csharp
public enum enum_DisplayKind
{
    DisplayKind_Value = 0x1,
    DisplayKind_Name = 0x2,
    DisplayKind_Type = 0x3,
};
```

## <a name="fields"></a>Campi
`DisplayKind_Value`\
Valore del campo.

`DisplayKind_Name`\
Nome del campo.

`DisplayKind_Type`\
Tipo di campo.

## <a name="requirements"></a>Requisiti
Intestazione: Ee.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
