---
title: require-npm
description: devinit tool require-npm.
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
ms.openlocfilehash: 3c8674c3fe0f05b0baa97e7851286f651361e3a37d6e524700e5ac4133887da2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390506"
---
# <a name="require-npm"></a>require-npm

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-npm` strumento viene usato per installare [NPM.](https://www.npmjs.com/)

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                       |
| [**Input**](#input)                              | string | Sì      | Specifica la versione NPM. Per [informazioni dettagliate,](#input) vedere Input di seguito.                           |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                  |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare la versione npm.

### <a name="additional-options"></a>Opzioni aggiuntive

Non utilizzato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-nodejs` strumento è installare la versione LTS più recente di npm.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `require-npm` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.jssu che installerà l'LTS di npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.jsin verrà installata una versione specifica di npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```