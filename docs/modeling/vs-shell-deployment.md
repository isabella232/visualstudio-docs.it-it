---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444999"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare quale funzionalità di Visual Studio è necessario interagire con il linguaggio specifico di dominio e come deve essere visualizzata tale soluzione. Per ulteriori informazioni sulla shell isolata di Visual Studio, vedere [Personalizzazione della shell isolata](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

Per impostare Visual Studio Shell come destinazione di distribuzione:

1. Nel progetto **DslPackage** aprire **source.extension.tt**.

2. Sotto `<SupportedProducts>` inserto:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell* con il nome del pacchetto shell isolato.
