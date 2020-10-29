---
title: App .NET Core
description: Repository di esempio che usa la devinit per installare un .NET Core SDK specifico.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028147"
---
# <a name="net-core-app"></a>App .NET Core

Vedere il repository [DevinitExample](https://github.com/microsoft/DevinitExample) per un esempio completo dell'uso di devinit per installare la versione di .NET Core SDK necessaria in codespaces.

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