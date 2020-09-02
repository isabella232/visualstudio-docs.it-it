---
title: Classe ContingentProperties-membri interni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414646"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - Membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Contiene proprietà aggiuntive per un <xref:System.Threading.Tasks.Task> oggetto.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Membri  
  
### <a name="fields"></a>Campi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|Elenco di attività figlio registrate con questa attività.|  
  
## <a name="remarks"></a>Osservazioni  
 Il .NET Framework inizializza i campi di questa classe solo quando sono necessari.  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
