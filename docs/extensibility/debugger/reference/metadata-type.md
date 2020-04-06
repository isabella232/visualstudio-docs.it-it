---
title: METADATA_TYPE . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afe5ea128775c7be0e48035ab4c7e7d370c9d233
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714302"
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
 ID dell'applicazione da cui proveniva il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.

 `guidModule`\
 GUID del modulo che contiene questo campo.

 `tokClass`\
 ID del token di metadati di questo tipo.

 [C]: `_mdToken` è `typedef` un per un `int`oggetto a 32 bit.

## <a name="remarks"></a>Osservazioni
 Questa struttura viene visualizzata come parte dell'unione `TYPE_INFO` nella struttura `TYPE_KIND_METADATA` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della struttura è impostato su (un valore dell'enumerazione [dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

 Il `tokClass` valore è un token di metadati che identifica in modo univoco un tipo. Per informazioni dettagliate su come interpretare i bit `CorTokenType` superiori dell'ID token di metadati, vedere l'enumerazione nel file corhdr.h in .NET Framework SDK.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
