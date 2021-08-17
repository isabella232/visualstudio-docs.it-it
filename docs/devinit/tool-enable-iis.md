---
title: enable-iis
description: devinit tool enable-iis.
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
ms.openlocfilehash: 3af597ef953f98b850638cb9ad0dabe721e5692951dd961f14cc977f47214414
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390677"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo strumento viene usato per abilitare le funzionalità di IIS e `enable-iis` installare il modulo ASP.NET Core [per](/aspnet/core/host-and-deploy/aspnet-core-module) lo ASP.NET sviluppo con IIS.

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                               |
| [**Input**](#input)                              | stringa | No       | Non usato.                                                                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato.                                                                           |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento prevede l'abilitazione delle funzionalità `enable-iis` IIS: IIS-WebServer, IIS-WebServerRole, IIS-WebSockets e IIS-WebAuthentication e quindi l'installazione della versione più recente del bundle di hosting ASP.NET che include il modulo ASP.NET Core.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `enable-iis` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.jsin che consentirà lo sviluppo iis:
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