---
title: npm-install
description: devinit tool npm-install.
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
ms.openlocfilehash: 233dd3b62e913d90e3b2b12db6c546aa0593455bf1a17b639f86aef9498dc826
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390621"
---
# <a name="npm-install"></a>npm-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `npm-install` strumento può essere usato per installare pacchetti [NPM.](https://www.npmjs.com/)

## <a name="usage"></a>Utilizzo

Se `input` entrambe le `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non farà nulla.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                                          |
| [**Input**](#input)                              | stringa | No       | Pacchetto da installare. Per [informazioni dettagliate,](#input) vedere Input di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No       | Opzioni aggiuntive da passare all'oggetto . Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.       |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare il nome del pacchetto da installare, ad esempio 'mongo'.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono pass-through diretto agli argomenti usati da [npm install](https://docs.npmjs.com/cli/install).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `npm-install` strumento è l'esecuzione `npm install` senza argomenti. Per [una descrizione di questo comportamento,](https://docs.npmjs.com/cli/v6/commands/npm-install) vedere la documentazione di npm.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `npm-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.jssu che installerà mongo:
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
