---
title: STEPKIND | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8d07f3d77d1f5f2c5deb8fcec75c6f4fac1fdf0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532574"
---
# <a name="stepkind"></a>STEPKIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [STEPKIND](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/stepkind).  
  
Specifica il tipo di passaggio per l'esecuzione di istruzioni.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
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
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
