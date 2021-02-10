---
title: App .NET Core
description: Repository di esempio che usa la devinit per installare un .NET Core SDK specifico.
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
ms.openlocfilehash: 364b3fbb0739891d1ce0f6341bb11af7f0ff76f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943585"
---
# <a name="net-core-app"></a>App .NET Core

Per un esempio completo dell'uso di devinit per installare la versione .NET Core SDK necessaria in codespaces, vedere il repository [devinit-example-DotNet-Core](https://github.com/microsoft/devinit-example-dotnet-core) .

## <a name="devinitjson"></a>.devinit.json

Contenuto del _.devinit.js_ nel file nella radice del repository.

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
