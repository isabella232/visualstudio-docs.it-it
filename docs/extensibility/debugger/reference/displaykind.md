---
title: DisplayKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DisplayKind enumeration
ms.assetid: 940968c5-6065-4bda-8ee6-c31597db4d71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 152f3b501aad6bba9e87e861346fa9ddb876a44d
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56315625"
---
# <a name="displaykind"></a>DisplayKind
Enumera i valori validi che rappresentano i tipi di informazioni da eseguire da un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) dell'oggetto e visualizzare all'utente.

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

#### <a name="parameters"></a>Parametri
DisplayKind_Value  
Valore del campo.

DisplayKind_Name  
Nome del campo.

DisplayKind_Type  
Tipo di campo.

## <a name="requirements"></a>Requisiti
Intestazione: EE.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
[Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)
