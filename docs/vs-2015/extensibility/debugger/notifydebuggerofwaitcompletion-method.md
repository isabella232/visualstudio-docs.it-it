---
title: Metodo NotifyDebuggerOfWaitCompletion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0548e1e791c41d806ccc222176ee571b037389
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968951"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>Metodo NotifyDebuggerOfWaitCompletion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Metodo segnaposto usato come destinazione un punto di interruzione dal debugger. Questo metodo non deve essere impostato come inline o ottimizzato.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
private void NotifyDebuggerOfWaitCompletion()  
```  
  
## <a name="remarks"></a>Note  
 Tutte le operazioni di join con un'attività devono chiamare questo metodo se i bit di notifica di debugger è impostato.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
