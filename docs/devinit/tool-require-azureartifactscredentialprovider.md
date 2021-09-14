---
title: require-azureartifactscredentialprovider
description: devinit tool require-azureartifactscredentialprovider.
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
ms.openlocfilehash: e5ba9847b09f06f853f48a0885de5e0d63664fac
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709847"
---
# <a name="require-azureartifactscredentialprovider"></a>require-azureartifactscredentialprovider

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-azureartifactscredentialprovider` strumento installa il Azure Artifacts Provider di credenziali. Il Azure Artifacts Provider di credenziali automatizza l'acquisizione delle credenziali necessarie per ripristinare NuGet pacchetti come parte del flusso di lavoro di sviluppo .NET. Altre informazioni su Azure Artifacts Provider di credenziali [qui.](https://github.com/microsoft/artifacts-credprovider/blob/master/README.md)

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                |
| [**Input**](#input)                              | stringa | No       | Non usato. Per informazioni [dettagliate, vedere l'input](#input) seguente. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                     |

### <a name="input"></a>Input

Non usato. Ignora qualsiasi input, se indicato.

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate così come sono al comando del provider di credenziali.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-azureartifactscredentialprovider` strumento è installare la versione più recente del Azure Artifacts Provider di credenziali.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-azureartifactscredentialprovider` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-azure-artifacts-credential-provider"></a>.devinit.json che installerà Azure Artifacts Provider di credenziali:
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
