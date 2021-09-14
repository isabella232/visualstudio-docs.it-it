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
ms.openlocfilehash: 011364e851670362ecaa9f4bdbfff965782ed706
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709853"
---
# <a name="npm-install"></a>npm-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `npm-install` strumento può essere usato per installare i pacchetti [NPM.](https://www.npmjs.com/)

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono `additionalOptions` omesse o vuote, lo strumento non farà nulla.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                                          |
| [**Input**](#input)                              | stringa | No       | Pacchetto da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No       | Opzioni aggiuntive da passare agli strumenti. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.       |

### <a name="input"></a>Input

La `input` proprietà viene usata per specificare il nome del pacchetto da installare, ad esempio 'mongo'.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di `additionalOptions` . Questi argomenti sono pass-through diretto agli argomenti usati da [npm install](https://docs.npmjs.com/cli/install).

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `npm-install` strumento è l'esecuzione `npm install` senza argomenti. Per [una descrizione di questo comportamento,](https://docs.npmjs.com/cli/v6/commands/npm-install) vedere la documentazione di npm.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `npm-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.json che installerà Mongo:
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
