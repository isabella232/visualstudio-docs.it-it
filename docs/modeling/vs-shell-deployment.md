---
title: Distribuzione della shell di Visual Studio
description: Informazioni su come una shell isolata consente di determinare Visual Studio funzionalità necessarie per interagire con il DSL e come deve apparire la soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: c521e68f8e26d636cfccaccc607c4a03a2d5b714
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123502"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare Visual Studio funzionalità necessarie per interagire con il linguaggio specifico di dominio e come deve apparire la soluzione. Per altre informazioni sulla shell Visual Studio isolata, vedere [Personalizzazione della shell isolata](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Per impostare una Visual Studio Shell come destinazione di distribuzione:

1. Nel progetto **DslPackage** aprire **source.extension.tt**.

2. In `<SupportedProducts>` inserisci:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell con* il nome del pacchetto della shell isolata.