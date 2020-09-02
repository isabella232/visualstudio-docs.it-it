---
title: EXCEPTION_STATE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149366"
---
# <a name="exception_state"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica lo stato dell'eccezione.  
  
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
 Arresta alla prima attivazione dell'eccezione. Quando si descrive un evento Exception, questo flag indica che l'evento Exception è un evento di eccezione first-chance.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Arresta alla seconda generazione dell'eccezione. Quando si descrive un evento Exception, indica che l'evento Exception è un evento di eccezione second-chance.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Arresta alla prima attivazione di un'eccezione in modalità utente. Quando si descrive un evento di eccezione, indica che l'evento di eccezione è un evento di eccezione utente first-chance.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Arrestare quando un'eccezione in modalità utente non viene rilevata. Quando si descrive un evento Exception, indica che l'evento Exception è un evento di eccezione in modalità utente non rilevata.  
  
 EXCEPTION_STOP_ALL  
 Arrestare in qualsiasi eccezione. Non utilizzato per la descrizione di un evento di eccezione.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 Quando si descrive un evento di eccezione, indica che non è possibile continuare l'eccezione da.  
  
 EXCEPTION_CODE_SUPPORTED  
 Indica che l'eccezione dispone di codice che lo supporta. Utilizzato per la visualizzazione di un'eccezione  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Indica che il codice di eccezione deve essere visualizzato in formato esadecimale. Utilizzato per la visualizzazione di un'eccezione.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Indica che il codice di eccezione supporta JustMyCode. Utilizzato per la visualizzazione di un'eccezione.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Indica che il debugger del codice gestito deve gestire le eccezioni. Se non è impostato, il debugger predefinito gestisce le eccezioni. Viene passato al metodo [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) e non viene utilizzato nella struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) .  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 OBSOLETO, NON USARE.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzato come `dwState` membro della struttura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) per indicare lo stato dell'eccezione e le operazioni che possono essere eseguite.  
  
 Questi valori vengono passati anche al metodo [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) per impostare lo stato di tutte le eccezioni.  
  
 Questi flag possono essere combinati con un OR bit per bit.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
