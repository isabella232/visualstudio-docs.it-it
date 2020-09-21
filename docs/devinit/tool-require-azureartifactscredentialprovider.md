---
title: require-azureartifactscredentialprovider
description: per lo strumento devinit è necessario azureartifactscredentialprovider.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 74e8775fb9dc864e8026f73e3bc75604dbf32e10
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810912"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

Lo `require-azureartifactscredentialprovider` strumento installa il provider di credenziali Azure Artifacts. Il provider di credenziali Azure Artifacts automatizza l'acquisizione delle credenziali necessarie per ripristinare i pacchetti NuGet come parte del flusso di lavoro di sviluppo .NET. Per altre informazioni, vedere Azure Artifacts provider di credenziali [qui](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md).

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                |
| [**input**](#input)                              | stringa | No       | Non usato. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                     |

### <a name="input"></a>Input

Non usato. Ignora eventuali input se specificati.

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate così come sono al comando del provider di credenziali.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-azureartifactscredentialprovider` strumento consiste nell'installare il provider di credenziali Azure Artifacts più recente.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that installs Azure Artifacts Credential Provider.'",
    "run": [
        {
            "tool": "require-azureartifactscredentialprovider",
            "comments": "Installs Azure Artifacts Credential Provider."
        }
    ]
}
```
