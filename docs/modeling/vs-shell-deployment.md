---
title: Distribuzione di Visual Studio Shell | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio
Una shell isolata consente di determinare quali Visual Studio funzionalità necessarie interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per ulteriori informazioni sulla shell di Visual Studio isolated, vedere [personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md). È possibile trovare ulteriori informazioni su come personalizzare la shell isolata in [personalizzazione Shell isolata](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione  
  
1.  Nel **DslPackage** progetto, aprire **source.extension.tt**.  
  
2.  In `<SupportedProducts>` inserire:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Sostituire *MyIsolatedShell* con il nome del pacchetto di shell isolata.