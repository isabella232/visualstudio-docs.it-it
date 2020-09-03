---
title: Campo m_stateObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149045"
---
# <a name="m_stateobject-field"></a>Campo m_stateObject
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Oggetto che rappresenta i dati che l'azione utilizzerà.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Osservazioni  
 Si tratta del `state` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo sottostante per la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> Proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
