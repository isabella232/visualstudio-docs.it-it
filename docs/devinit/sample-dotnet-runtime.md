---
title: Runtime di .NET Core
description: Personalizzazione di esempio con il devinit per il repository DotNet/Runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 477a498059be6d1ee5637a704512fd49b62e11b6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809111"
---
# <a name="net-core-runtime"></a>Runtime di .NET Core

Questo esempio illustra come personalizzare il runtime [DotNet/Runtime](https://github.com/dotnet/runtime) di .NET Core per eseguire automaticamente il provisioning con gli spazi dei codebase di [GitHub](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Questo script viene chiamato da _PostCloneSetup.ps1_ e può essere eseguito anche localmente per configurare il repository. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_.

```batch
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Il file di _packages.config_ è un file di [cioccolato](https://chocolatey.org/) che definisce l'elenco di pacchetti di cioccolato da installare. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.js

Contenuto del [_.devinit.jssu_](devinit-json.md) file. Questo file deve trovarsi nella stessa cartella del file _.devcontainer.js_ .

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js

Contenuto del _.devcontainer.js_ nel file nella radice del repository.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
