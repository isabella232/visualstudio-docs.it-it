---
title: CONSTRUCTOR_ENUM | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b435507c84d697ef27a2b37d6153a53dbe13cb3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206076"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Seleziona tipi diversi di costruttori.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Membri  
 crAll  
 Seleziona tutti i costruttori.  
  
 crNonStatic  
 Seleziona i costruttori non statici.  
  
 crStatic  
 Seleziona i costruttori statici.  
  
## <a name="remarks"></a>Osservazioni  
 Passato come argomento al metodo [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) .  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
