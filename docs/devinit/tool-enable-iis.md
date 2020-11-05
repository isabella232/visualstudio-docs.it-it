---
title: enable-iis
description: Abilitazione dello strumento devinit-IIS.
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
ms.openlocfilehash: ec326871f5565ecaabdc8cda369b36df14029414
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399830"
---
# <a name="enable-iis"></a>enable-iis

Lo `enable-iis` strumento viene usato per abilitare le funzionalità di IIS e per installare il [modulo ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) per lo sviluppo di ASP.NET con IIS.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                               |
| [**input**](#input)                              | stringa | No       | Non usato.                                                                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato.                                                                           |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `enable-iis` strumento consiste nell'abilitare le funzionalità IIS: IIS-Webserver, IIS-WebServerRole, IIS-WebSocket e IIS-webauthentication, quindi installare la versione più recente del bundle di hosting ASP.NET che include il modulo ASP.NET Core. 

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```