---
title: Runtime di .NET Core
description: Personalizzazione di esempio con devinit per il repo dotnet/runtime.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 3c8ba55338a957239732f7a45a46acbcb3d9c95bf980efc5e49af4e898cbfac1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452859"
---
# <a name="net-core-runtime"></a>Runtime di .NET Core

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio illustra come personalizzare il runtime di .NET Core [dotnet/runtime](https://github.com/dotnet/runtime) per il provisioning automatico [GitHub Codespaces.](https://github.com/features/codespaces)

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Questo script viene chiamato da _PostCloneSetup.ps1_ e può anche essere eseguito in locale per configurare il repository. Questo file deve essere nella stessa cartella di _.devcontainer.jsin_.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Il _packages.config_ è un file [Chocolatey](https://chocolatey.org/) che definisce l'elenco di pacchetti Chocolatey da installare. Questo file deve essere nella stessa cartella di _.devcontainer.jsin_.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Contenuto del [`.devinit.json`](devinit-json.md) file. Questo file deve essere nella stessa cartella in cui si.devcontainer.js _file._

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

## <a name="devcontainerjson"></a>.devcontainer.jssu

Contenuto del.devcontainer.js _nel_ file nella radice del repo.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
