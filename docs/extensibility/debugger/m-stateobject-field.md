---
title: Campo m_stateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8718a45f0a2d8ef3075a9c390a756e3ec50062f9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028712"
---
# <a name="mstateobject-field"></a>campo m_stateObject
Oggetto che rappresenta i dati che verrà usato l'azione.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in *mscorlib. dll*)  
  
 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Note  
 Questo è il `state` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo sottostante per il <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)