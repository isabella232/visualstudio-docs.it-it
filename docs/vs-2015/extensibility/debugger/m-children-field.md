---
title: Campo m_children | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a681f3a58fddbb136383a1259aa5e4c0c3b96b69
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289633"
---
# <a name="mchildren-field"></a>Campo m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'elenco delle attività figlio che sono registrati con questa attività.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Note  
 Durante l'esecuzione dell'attività, solo il thread che esegue l'attività deve accedere a questa matrice.  
  
 Se l'attività è stata completata, altri thread possa accedere a questo campo, purché non aggiunge nulla ad esso né rimuovere qualsiasi elemento da quest'ultimo.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

