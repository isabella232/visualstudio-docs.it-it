---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566673"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare quali Visual Studio la funzionalità è necessario interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della Shell isolata](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione

1.  Nel **DslPackage** progetto aprire **source.extension.tt**.

2.  In `<SupportedProducts>` inserire:

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Sostituire *MyIsolatedShell* con il nome del pacchetto shell isolata.