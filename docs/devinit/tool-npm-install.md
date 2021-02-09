---
title: npm-install
description: strumento devinit NPM-install.
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
ms.openlocfilehash: 4ed32fba72a50adf8c657cc34de9cd61d01e7abc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874526"
---
# <a name="npm-install"></a>npm-install

Lo `npm-install` strumento può essere usato per installare i pacchetti [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non eseguirà alcuna operazione.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                                          |
| [**input**](#input)                              | stringa | No       | Pacchetto da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No       | Opzioni aggiuntive da passare allo strumento. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare il nome del pacchetto da installare, ad esempio "Mongo".

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono passthrough diretto per gli argomenti usati dall' [installazione di NPM](https://docs.npmjs.com/cli/install).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `npm-install` strumento è l'esecuzione `npm install` senza argomenti. Per una descrizione di questo comportamento, vedere [la documentazione di NPM](https://docs.npmjs.com/cli/v6/commands/npm-install) .

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `npm-install` usando un `.devinit.json` .

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.jssu che installerà Mongo:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
