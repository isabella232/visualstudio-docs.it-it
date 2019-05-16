---
title: Distribuzione della Shell di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bfe88d7e7d742eb67273d307c3a8e72e9a85833
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704042"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una shell isolata consente di determinare quali Visual Studio la funzionalità è necessario interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md). È possibile trovare altre informazioni sulla personalizzazione della shell isolata in [personalizzazione della Shell isolata](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione  
  
1. Nel **DslPackage** progetto aprire **source.extension.tt**.  
  
2. In `<SupportedProducts>` inserire:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Sostituire *MyIsolatedShell* con il nome del pacchetto shell isolata.
