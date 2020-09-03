---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad4b6a06a2a145daa85d780f4d23dfac9bebf7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205107"
---
# <a name="pdb_type"></a>PDB_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura specifica le informazioni su un tipo di campo tratto da un simbolo PDB.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```csharp  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 ulAppDomainID  
 ID dell'applicazione da cui è arrivato il simbolo. Viene utilizzato per identificare in modo univoco un'istanza dell'applicazione.  
  
 guidModule  
 GUID del modulo che contiene questo campo.  
  
 symid  
 ID del simbolo che corrisponde a questo campo.  
  
## <a name="remarks"></a>Osservazioni  
 Questa struttura viene visualizzata come parte dell'Unione nella struttura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando il `dwKind` campo della `TYPE_INFO` struttura è impostato su `TYPE_KIND_PDB` (un valore dell'enumerazione [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
