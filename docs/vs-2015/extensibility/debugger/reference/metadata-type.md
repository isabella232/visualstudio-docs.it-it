---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546824"
---
# <a name="metadata_type"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura specifica le informazioni su un tipo di campo tratto dai metadati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 ID dell'applicazione da cui è arrivato il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.  
  
 guidModule  
 GUID del modulo che contiene questo campo.  
  
 tokClass  
 ID del token di metadati di questo tipo.  
  
 [C++] `_mdToken` è un oggetto `typedef` per un oggetto a 32 bit `int` .  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene visualizzata come parte dell'Unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della `TYPE_INFO` struttura è impostato su `TYPE_KIND_METADATA` (un valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
 Il `tokClass` valore è un token di metadati che identifica in modo univoco un tipo. Per informazioni dettagliate su come interpretare i bit superiori dell'ID del token di metadati, vedere l' `CorTokenType` enumerazione nel file corhdr. h nell' [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
