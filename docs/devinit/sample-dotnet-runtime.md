---
title: Runtime di .NET Core
description: Esempio di personalizzazione con devinit per il repo dotnet/runtime.
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
ms.openlocfilehash: d703e71b6f8ab57ab07c4143fdd5435585c6004c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710352"
---
# <a name="net-core-runtime"></a>Runtime di .NET Core

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio illustra come personalizzare il runtime [dotnet/runtime](https://github.com/dotnet/runtime) di .NET Core per il provisioning automatico con GitHub [Codespace.](https://github.com/features/codespaces)

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Questo script viene chiamato da _PostCloneSetup.ps1_ e può essere eseguito anche in locale per configurare il repository. Questo file deve essere nella stessa cartella _di .devcontainer.json._

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Il _packages.config_ file è un file [Chocolatey](https://chocolatey.org/) che definisce l'elenco di pacchetti Chocolatey da installare. Questo file deve essere nella stessa cartella _di .devcontainer.json._

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Contenuto del [`.devinit.json`](devinit-json.md) file. Questo file deve essere nella stessa cartella del file _con estensione devcontainer.json._

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

## <a name="devcontainerjson"></a>.devcontainer.json

Contenuto del file _devcontainer.json_ nella radice del repo.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
