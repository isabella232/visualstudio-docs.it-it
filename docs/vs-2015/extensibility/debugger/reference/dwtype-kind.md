---
title: dwTYPE_KIND | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62f4f404838a3d22dfd25a8c9846257930a45118
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794829"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica come interpretare il tipo di un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto.  
  
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
 Il [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) unione deve essere interpretato come una [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) struttura.  
  
 TYPE_KIND_PDB  
 Il `TYPE_INFO` unione deve essere interpretata come un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) struttura.  
  
 TYPE_KIND_BUILT  
 Il `TYPE_INFO` unione deve essere interpretata come un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) struttura.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono visualizzati nei `dwKind` campo del [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) strutturare e vengono usate per determinare come interpretare il `type` membro dell'unione. Il `TYPE_INFO` struttura viene restituita da una chiamata per il [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)

