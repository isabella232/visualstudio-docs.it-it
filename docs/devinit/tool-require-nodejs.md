---
title: require-NodeJS
description: per lo strumento devinit è necessario NodeJS.
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
ms.openlocfilehash: 6bc2de2e497bd58cfc036e74af3968a2f70d1f52
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808418"
---
# <a name="require-nodejs"></a>require-NodeJS

Lo `require-nodejs` strumento viene usato per installare il [Node.js](https://nodejs.org/) tramite un file MSI distribuito dall'organizzazione Node.js.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                     |
| [**input**](#input)                              | stringa | No       | Versione di Node.JS da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.          |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare la versione del Node.js. È possibile trovare un elenco di versioni nella [ pagina di downloadNode.js](https://nodejs.org/en/download/). Il numero di versione completo è obbligatorio. minor. Path (ad esempio, 14.4.0) se viene omesso, l'installazione avrà esito negativo.

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono pass-through diretto al programma di installazione MSI per Node.js.  

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-nodejs` strumento consiste nell'installare la versione LTS più recente del nodo, come descritto nel [sito Web](https://nodejs.org/en/download/)Node.JS.

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
