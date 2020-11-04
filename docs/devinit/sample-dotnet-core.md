---
title: App .NET Core
description: Repository di esempio che usa la devinit per installare un .NET Core SDK specifico.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 35971ac1fde5fc272f22579cc6640cbea6724db5
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344518"
---
# <a name="net-core-app"></a>App .NET Core

Vedere il repository [DotnetCoreDevinitExample](https://github.com/microsoft/DotnetCoreDevinitExample) per un esempio completo dell'uso di devinit per installare la versione di .NET Core SDK necessaria in codespaces.

## <a name="devinitjson"></a>.devinit.json

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

## <a name="devcontainerjson"></a>.devcontainer.js

Contenuto del _.devcontainer.js_ nel file nella radice del repository.

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

Contenuto del _global.js_ nel file nella radice del repository.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
