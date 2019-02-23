---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a39ce54d1cb1fb1a3773b4241be35214421f08a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709993"
---
# <a name="metadatatype"></a>METADATA_TYPE
Questa struttura consente di specificare informazioni su un tipo di campo impiegato dai metadati.

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

#### <a name="parameters"></a>Parametri
 ulAppDomainID

 ID dell'applicazione da cui proviene il simbolo. Ciò consente di identificare in modo univoco un'istanza dell'applicazione.

 guidModule

 Il GUID del modulo che contiene questo campo.

 tokClass

 L'ID del token dei metadati di questo tipo.

 [C++] `_mdToken` è un `typedef` un 32-bit `int`.

## <a name="remarks"></a>Note
 Questa struttura viene visualizzato come parte dell'unione nel [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) struttura quando il `dwKind` campo il `TYPE_INFO` struttura è impostata su `TYPE_KIND_METADATA` (un valore compreso il [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumerazione).

 Il `tokClass` valore è un token di metadati che identifica un tipo. Per informazioni dettagliate su come interpretare i bit più significativi dell'ID del token di metadati, vedere la `CorTokenType` enumerazione nel file corhdr. h di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)