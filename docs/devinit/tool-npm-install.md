---
title: npm-install
description: strumento devinit NPM-install.
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
ms.openlocfilehash: 432c2a6c532e95e7d0e3e4cb22c87930031f5907
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400295"
---
# <a name="npm-install"></a>npm-install

Lo `npm-install` strumento può essere usato per installare i pacchetti [NPM](https://www.npmjs.com/) .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non eseguirà alcuna operazione.

| Nome                                             | Type   | Obbligatoria | valore                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                                          |
| [**input**](#input)                              | string | Sì      | Pacchetto da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No       | Opzioni aggiuntive da passare allo strumento. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare il nome del pacchetto da installare, ad esempio "Mongo".

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono passthrough diretto per gli argomenti usati dall' [installazione di NPM](https://docs.npmjs.com/cli/install).

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will install the mongo NPM package (https://www.npmjs.com/package/mongo).",
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
