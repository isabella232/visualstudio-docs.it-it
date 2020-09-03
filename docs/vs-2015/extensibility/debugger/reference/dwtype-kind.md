---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f37fb773a07291a883f5cb65e4cb4ac840a87a14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198785"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica come interpretare il tipo di un oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 TYPE_KIND_METADATA  
 L'Unione [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) deve essere interpretata come una struttura di [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .  
  
 TYPE_KIND_PDB  
 L' `TYPE_INFO` Unione deve essere interpretata come una struttura [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .  
  
 TYPE_KIND_BUILT  
 L' `TYPE_INFO` Unione deve essere interpretata come una struttura [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) .  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono visualizzati nel `dwKind` campo della struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) e vengono utilizzati per determinare come interpretare il `type` membro di Unione. La `TYPE_INFO` struttura viene restituita da una chiamata al metodo [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
