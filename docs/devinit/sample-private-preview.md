---
title: Anteprima privata
description: Personalizzazioni di esempio usate nel repository di Visual Studio preview beta di GitHub codespaces.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 61ef0a0575e5b86ab7cbd7c17e37c552c0c14388
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005631"
---
# <a name="private-preview"></a>Anteprima privata

Questo esempio illustra come personalizzare uno spazio dei caratteri per Visual Studio in modo che abbia le stesse funzionalità della beta privata iniziale di [GitHub codespaces](https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.json

Contenuto del [_.devinit.jssu_](devinit-json.md) file. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_.

```json
{
    "run": [
        {
            "tool": "choco-install",
            "input": "python2"
        },
        {
            "tool": "choco-install",
            "input": "python3"
        },
        {
            "tool": "require-dotnetcoresdk",
            "input": "2.1.807"
        },
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-azurecli"
        },
        {
            "tool": "require-nodejs"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        },
        {
            "tool": "require-vcpkg"
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
