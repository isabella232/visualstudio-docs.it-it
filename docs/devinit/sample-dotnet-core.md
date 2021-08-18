---
title: App .NET Core
description: Repository di esempio che usa devinit per installare una specifica .NET Core SDK.
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
ms.openlocfilehash: c56665df760338975e334533bc3ddfdcd4f34434e01a3e17ca8d5d9440679856
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452940"
---
# <a name="net-core-app"></a>App .NET Core

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Vedere il repository [devinit-example-dotnet-core](https://github.com/microsoft/devinit-example-dotnet-core) per un esempio completo dell'uso di devinit per installare la versione .NET Core SDK in Codespaces.

## <a name="devinitjson"></a>.devinit.json

Contenuto del.devinit.js _nel_ file nella radice del repo.

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

## <a name="devcontainerjson"></a>.devcontainer.jssu

Contenuto del.devcontainer.js _nel_ file nella radice del repo.

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

Contenuto delglobal.js _nel_ file nella radice del repo.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
