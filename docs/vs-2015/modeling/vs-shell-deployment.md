---
title: Distribuzione della Shell di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532913"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [distribuzione di Visual Studio Shell](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Una shell isolata consente di determinare quali Visual Studio la funzionalità è necessario interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md). È possibile trovare altre informazioni sulla personalizzazione della shell isolata in [personalizzazione della Shell isolata](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione  
  
1.  Nel **DslPackage** progetto aprire **source.extension.tt**.  
  
2.  In `<SupportedProducts>` inserire:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Sostituire *MyIsolatedShell* con il nome del pacchetto shell isolata.



