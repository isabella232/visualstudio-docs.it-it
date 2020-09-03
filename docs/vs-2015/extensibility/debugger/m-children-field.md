---
title: Campo m_children | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149066"
---
# <a name="m_children-field"></a>Campo m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Elenco di attività figlio registrate con questa attività.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Osservazioni  
 Mentre l'attività è in esecuzione, solo il thread che esegue l'attività deve accedere a questa matrice.  
  
 Se l'attività viene completata, gli altri thread possono accedere a questo campo purché non aggiungano nulla o non rimuovano nulla.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
