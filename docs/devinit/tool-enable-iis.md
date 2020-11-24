---
title: enable-iis
description: Abilitazione dello strumento devinit-IIS.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b4b7c3f9681dd636ef88a5cd9f59c84c4ecac89c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440361"
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
Di seguito è riportato un esempio di come eseguire `enable-iis` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.jssu che consente lo sviluppo di IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```