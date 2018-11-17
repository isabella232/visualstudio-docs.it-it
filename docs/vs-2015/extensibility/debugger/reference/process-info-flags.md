---
title: PROCESS_INFO_FLAGS | Microsoft Docs
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
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 453c976ec4dd1c0c0b1c1e67592f840c17a9ac9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726791"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrivono o specificano le proprietà di un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```csharp  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## <a name="members"></a>Membri  
 PIFLAG_SYSTEM_PROCESS  
 Indica che il processo è un processo di sistema.  
  
 PIFLAG_DEBUGGER_ATTACHED  
 Indica che il processo viene eseguito il debug da un debugger. Potrebbe essere un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger o potrebbe essere alcuni altri debugger, ad esempio, WinDbg.  
  
 PIFLAG_PROCESS_STOPPED  
 Indica che il processo viene arrestato. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e versioni successive.  
  
 PIFLAG_PROCESS_RUNNING  
 Indica che il processo è in esecuzione. Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato. Disponibile in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e versioni successive.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `Flags` membro della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)

