---
title: STEPKIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a24513e5d047501417e4c61285662f7167241e3f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970095"
---
# <a name="stepkind"></a>STEPKIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Specifica il tipo di passaggio per l'esecuzione di istruzioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Membri  
 STEP_INTO  
 Passaggi in una funzione.  
  
 STEP_OVER  
 Istruzioni/routine di una funzione.  
  
 STEP_OUT  
 Esce dalla funzione.  
  
 STEP_BACKWARDS  
 Procedura con le versioni precedenti in una funzione.  
  
## <a name="remarks"></a>Note  
 Passato come argomento per il [passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
