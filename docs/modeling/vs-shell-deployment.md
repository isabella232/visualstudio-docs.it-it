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
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946988"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare quali Visual Studio funzionalità necessarie interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per ulteriori informazioni sulla shell di Visual Studio isolated, vedere [personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una Shell di Visual Studio come destinazione di distribuzione

1.  Nel **DslPackage** progetto, aprire **source.extension.tt**.

2.  In `<SupportedProducts>` inserire:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Sostituire *MyIsolatedShell* con il nome del pacchetto di shell isolata.