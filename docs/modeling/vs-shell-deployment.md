---
title: Distribuzione della shell di Visual Studio
description: Informazioni su come una shell isolata consente di determinare Visual Studio funzionalità necessarie per interagire con il DSL e come deve apparire la soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388308"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare Visual Studio funzionalità necessarie per interagire con il linguaggio specifico di dominio e come deve apparire la soluzione. Per altre informazioni sulla shell Visual Studio isolata, vedere [Personalizzazione della shell isolata](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Per impostare una Visual Studio Shell come destinazione della distribuzione:

1. Nel progetto **DslPackage** aprire **source.extension.tt**.

2. In `<SupportedProducts>` inserisci:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell* con il nome del pacchetto della shell isolata.