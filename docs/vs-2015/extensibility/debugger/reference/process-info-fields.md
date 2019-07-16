---
title: PROCESS_INFO_FIELDS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7700670774dcb38b054cf28275f64c0c3046f741
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205032"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specificare il tipo di informazioni da recuperare per un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Members  
 PIF_FILE_NAME  
 Initialize/usare la `bstrFileName` campo le [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura.  
  
 PIF_BASE_NAME  
 Initialize/usare la `bstrBaseName` campo il `PROCESS_INFO` struttura.  
  
 PIF_TITLE  
 Initialize/usare la `bstrTitle` campo il `PROCESS_INFO` struttura.  
  
 PIF_PROCESS_ID  
 Initialize/usare la `ProcessId` campo il `PROCESS_INFO` struttura.  
  
 PIF_SESSION_ID  
 Initialize/usare la `dwSessionId` campo il `PROCESS_INFO` struttura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Initialize/usare la `bstrAttachedSessionName` campo il `PROCESS_INFO` struttura.  
  
 PIF_CREATION_TIME  
 Initialize/usare la `CreationTime` campo il `PROCESS_INFO` struttura.  
  
 PIF_FLAGS  
 Initialize/usare la `Flags` campo il `PROCESS_INFO` struttura.  
  
 PIF_ALL  
 Compila tutti i campi.  
  
## <a name="remarks"></a>Note  
 Passato per il [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) metodo per indicare quali campi della [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) struttura devono essere inizializzate.  
  
 Usato anche in `Fields` campo il `PROCESS_INFO` struttura per indicare quali campi vengono usati e valido.  
  
 Questi flag possono essere combinati con un bit per bit `OR`.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
