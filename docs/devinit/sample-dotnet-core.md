---
title: App .NET Core
description: Repository di esempio che usa devinit per installare un .NET Core SDK.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b3e25835f305a96b2205fc96cc0200d68ad033af
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710353"
---
# <a name="net-core-app"></a>App .NET Core

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Vedere il repository [devinit-example-dotnet-core](https://github.com/microsoft/devinit-example-dotnet-core) per un esempio completo dell'uso di devinit per installare la versione .NET Core SDK necessaria in Codespaces.

## <a name="devinitjson"></a>.devinit.json

Contenuto del file _devinit.json_ nella radice del repo.

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.json

Contenuto del file _devcontainer.json_ nella radice del repo.

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

Contenuto del file _global.json_ nella radice del repo.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
