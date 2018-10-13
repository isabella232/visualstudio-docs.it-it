---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed69bf8c54d3b428907b4dbe0636f2966254de75
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253636"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Notifica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che è necessario unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e controllare se vi sono modifiche della cache MEF.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esegue questo comando automaticamente quando si installa un pacchetto VSIX. È consigliabile eseguire `devenv.exe /updateconfiguration` dopo l'applicazione di patch ai file in modo che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aggiorni la cache MEF. Ciò consente di valutare se la correzione è adeguata.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente indica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] di unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e di controllare se vi sono modifiche della cache MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



