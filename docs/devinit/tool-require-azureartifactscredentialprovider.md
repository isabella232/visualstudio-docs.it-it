---
title: require-azureartifactscredentialprovider
description: per lo strumento devinit è necessario azureartifactscredentialprovider.
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
ms.openlocfilehash: a23ffc8a32df89a1ec19b1b26d0f8fab491c3a1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948502"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

Lo `require-azureartifactscredentialprovider` strumento installa il provider di credenziali Azure Artifacts. Il provider di credenziali Azure Artifacts automatizza l'acquisizione delle credenziali necessarie per ripristinare i pacchetti NuGet come parte del flusso di lavoro di sviluppo .NET. Per altre informazioni, vedere Azure Artifacts provider di credenziali [qui](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                |
| [**input**](#input)                              | stringa | No       | Non usato. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                     |

### <a name="input"></a>Input

Non usato. Ignora eventuali input se specificati.

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate così come sono al comando del provider di credenziali.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-azureartifactscredentialprovider` strumento prevede l'installazione della versione più recente del provider di credenziali Azure Artifacts.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-azureartifactscredentialprovider` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.jsin che installerà Azure Artifacts provider di credenziali:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
        }
    ]
}
```
