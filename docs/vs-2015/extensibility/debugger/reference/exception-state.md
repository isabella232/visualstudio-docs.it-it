---
title: EXCEPTION_STATE | Microsoft Docs
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
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99f78b2de9b68b638feaf3f84eba4cc12c742ed0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879727"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica lo stato di eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Membri  
 EXCEPTION_NONE  
 Non arrestare in corrispondenza dell'eccezione.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Arresto generazione dell'evento prima dell'eccezione. Quando si descrive un evento di eccezione, questo flag indica che l'evento dell'eccezione è un evento di eccezioni first-chance.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Interrompere alla seconda generazione dell'eccezione. Quando si descrive un evento di eccezione, indica che l'evento dell'eccezione è un evento di eccezione second-chance.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Termina prima attivazione di un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento dell'eccezione è un evento di eccezione utente first-chance.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Interrompi quando non viene intercettata un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento dell'eccezione è un evento di eccezione in modalità utente non rilevate.  
  
 EXCEPTION_STOP_ALL  
 Arrestare qualsiasi eccezione. Non utilizzato quando si descrive un evento di eccezione.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Quando si descrive un evento di eccezione, indica che l'eccezione non può essere ripreso da.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indica che l'eccezione contiene codice che lo supporta. Utilizzati per la visualizzazione di un'eccezione  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indica che il codice di eccezione deve essere visualizzato in formato esadecimale. Utilizzati per la visualizzazione di un'eccezione.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indica che il codice di eccezione supporta JustMyCode. Utilizzati per la visualizzazione di un'eccezione.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indica che il debugger di codice gestito deve gestire le eccezioni. Se non impostato, il debugger predefinito gestisce le eccezioni. Viene passato al [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metodo e non utilizzata nel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
## <a name="remarks"></a>Note  
 Utilizzato come il `dwState` membro della [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura per indicare lo stato di eccezione e ciò che può essere eseguita su di esso.  
  
 Questi valori vengono passati anche per il [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) metodo per impostare lo stato di tutte le eccezioni.  
  
 Questi flag possono essere combinati con un OR bit per bit.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)

