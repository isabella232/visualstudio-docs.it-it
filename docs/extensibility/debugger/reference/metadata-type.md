---
description: La METADATA_TYPE specifica informazioni su un tipo di campo derivato dai metadati.
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0042109e1d71506117f2e8029d8eef6065703f02
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125309"
---
# <a name="metadata_type"></a>METADATA_TYPE
Questa struttura specifica le informazioni su un tipo di campo derivato dai metadati.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagTYPE_METADATA {
   ULONG32  ulAppDomainID;
   GUID     guidModule;
   _mdToken tokClass;
} METADATA_TYPE;
```

```csharp
public struct METADATA_TYPE {
   public uint ulAppDomainID;
   public Guid guidModule;
   public int  tokClass;
};
```

## <a name="parameters"></a>Parametri
 `ulAppDomainID`\
 ID dell'applicazione da cui deriva il simbolo. Viene usato per identificare in modo univoco un'istanza dell'applicazione.

 `guidModule`\
 GUID del modulo che contiene questo campo.

 `tokClass`\
 ID del token di metadati di questo tipo.

 [C++] `_mdToken` è un `typedef` oggetto per un oggetto a 32 `int` bit.

## <a name="remarks"></a>Commenti
 Questa struttura viene visualizzata come parte dell'unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il campo della struttura è impostato su (un valore `dwKind` dell'enumerazione `TYPE_INFO` `TYPE_KIND_METADATA` [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) tabella).

 Il `tokClass` valore è un token di metadati che identifica in modo univoco un tipo. Per informazioni dettagliate su come interpretare i bit superiori dell'ID del token di metadati, vedere l'enumerazione nel `CorTokenType` file corhdr.h in .NET Framework SDK.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
