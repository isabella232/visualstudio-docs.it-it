---
title: require-nodejs
description: devinit tool require-nodejs.
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
ms.openlocfilehash: 9aecdbfc113f21c719a210b86e6df64f7da725c274f7741414561a6ebbdb530f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343210"
---
# <a name="require-nodejs"></a>require-nodejs

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo strumento viene usato per installare ilNode.jstramite un'applicazione del servizio msi `require-nodejs` distribuita dall'organizzazione [](https://nodejs.org/) Node.js servizio.

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                     |
| [**Input**](#input)                              | stringa | No       | Versione di Node.JS da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito. |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.          |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare la Node.js predefinita. Un elenco delle versioni è disponibile nella pagina [Node.js download.](https://nodejs.org/en/download/) Il numero di versione completo è necessario Major.Minor.Path (ad esempio 14.4.0) se vengono omessi, l'installazione avrà esito negativo.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono pass-through diretto al programma di installazione MSI per Node.js.  

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è l'installazione della versione LTS più recente di Node, come descritto in dettaglio nel sito `require-nodejs` Web Node.JS [.](https://nodejs.org/en/download/)

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `require-nodejs` usando `.devinit.json` un oggetto . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.jsin verrà installato l'LTS di Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.jsin verrà installata una versione specifica di Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
