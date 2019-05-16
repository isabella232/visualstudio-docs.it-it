---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2f20463cd91148143a1d3fb7f7de5cc1649d683c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689347"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che è necessario unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e controllare se vi sono modifiche della cache MEF.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esegue questo comando automaticamente quando si installa un pacchetto VSIX. È consigliabile eseguire `devenv.exe /updateconfiguration` dopo l'applicazione di patch ai file in modo che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aggiorni la cache MEF. Ciò consente di valutare se la correzione è adeguata.  
  
## <a name="example"></a>Esempio  
 La riga di comando seguente indica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] di unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e di controllare se vi sono modifiche della cache MEF.  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
