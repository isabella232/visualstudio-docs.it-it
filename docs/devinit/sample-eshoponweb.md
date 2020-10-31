---
title: eShopOnWeb
description: Esempio di personalizzazione usando devinit per il repository DotNet-Architecture/eShopOnWeb.
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
ms.openlocfilehash: e886ea23a8f4f0815773f704d1d8274fced610df
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134594"
---
# <a name="eshoponweb"></a>eShopOnWeb

Questo esempio illustra come personalizzare l'esempio di architettura DotNet [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) per eseguire automaticamente il provisioning con gli [spazi dei codespace di GitHub](https://github.com/features/codespaces).

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Questo script viene chiamato da _PostCloneSetup.ps1_ e può essere eseguito anche localmente per configurare il repository. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_ .

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Contenuto del [_.devinit.jssu_](devinit-json.md) file. Questo file deve trovarsi nella stessa cartella del _.devcontainer.js_ .

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.js

Contenuto del _.devcontainer.js_ nel file nella radice del repository.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
