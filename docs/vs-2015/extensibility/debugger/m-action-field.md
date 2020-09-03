---
title: Campo m_action | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1506827a1132c659b1082d0f3d4aed9a21b417d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149104"
---
# <a name="m_action-field"></a>Campo m_action
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Delegato che rappresenta il codice da eseguire nell' <xref:System.Threading.Tasks.Task> oggetto.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field assembly object m_action  
```  
  
## <a name="remarks"></a>Osservazioni  
 Si tratta del `action` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
