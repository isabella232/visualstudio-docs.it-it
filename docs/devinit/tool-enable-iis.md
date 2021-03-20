---
title: enable-iis
description: Abilitazione dello strumento devinit-IIS.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671630"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione agli spazi dei codebase di GitHub da Visual Studio 2019 non sarà più supportata e l'anteprima privata è stata conclusa. Ci stiamo concentrando sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e per le soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro di Visual Studio. Come parte di questo `devinit` e gli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio per informazioni sulle future anteprime e informazioni di roadmap.

Lo `enable-iis` strumento viene usato per abilitare le funzionalità di IIS e per installare il [modulo ASP.NET Core](/aspnet/core/host-and-deploy/aspnet-core-module) per lo sviluppo di ASP.NET con IIS.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                               |
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