---
title: Abilita-IIS
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
ms.openlocfilehash: 245ea76f988b9a9e320a51ba6b2df01382668cc0
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127839"
---
# <a name="enable-iis"></a>Abilita-IIS

Lo `enable-iis` strumento viene usato per abilitare le funzionalità di IIS e per installare il [modulo ASP.NET Core](https://docs.microsoft.com/aspnet/core/host-and-deploy/aspnet-core-module) per lo sviluppo di ASP.NET con IIS.

## <a name="usage"></a>Uso

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
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```
