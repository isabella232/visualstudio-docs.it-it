---
title: eShopOnWeb
description: Esempio di personalizzazione con devinit per il repo dotnet-architecture/eShopOnWeb.
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
ms.openlocfilehash: 1356cf2654adfb78fcff61c9f9dab95f1fdbe913
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710348"
---
# <a name="eshoponweb"></a>eShopOnWeb

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Questo esempio illustra come personalizzare l'esempio di architettura dotnet [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) per il provisioning automatico con GitHub [Codespace.](https://github.com/features/codespaces)

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Questo script viene chiamato _da_ PostCloneSetup.ps1e può anche essere eseguito in locale per configurare il repository. Questo file deve essere nella stessa cartella _di .devcontainer.json._

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

Contenuto del [`.devinit.json`](devinit-json.md) file. Questo file deve essere nella stessa cartella _di .devcontainer.json._

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

## <a name="devcontainerjson"></a>.devcontainer.json

Contenuto del file _devcontainer.json_ nella radice del repo.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
