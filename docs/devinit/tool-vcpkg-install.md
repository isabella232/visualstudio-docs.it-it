---
title: vcpkg-install
description: devinit tool vcpkg-install.
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
ms.openlocfilehash: 8a4cbe6bd1da12985da87d2f872dc74f988ef213
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709840"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `vcpkg-install` strumento viene usato per acquisire librerie C/C++ (denominate porte) [usando](https://github.com/microsoft/vcpkg)vcpkg .

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                                   |
| [**Input**](#input)                              | string | Sì      | Pacchetti da installare. Per [informazioni dettagliate,](#input) vedere Input di seguito.                       |
| [**additionalOptions**](#additional-options)     | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                        |

### <a name="input"></a>Input

La `input` proprietà deve essere dell'oggetto da installare o un elenco di nomi separati `name` da spazi per installare più `vcpkg` pacchetti. Un elenco delle porte disponibili è disponibile nel [vcpkg GitHub.](https://github.com/microsoft/vcpkg/tree/master/ports)

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni aggiuntive vengono passate direttamente [al comando vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) e sono documentate nel [vcpkg GitHub.](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `vcpkg-install` strumento è l'errore come `input` richiesto.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito sono riportati esempi di come eseguire `vcpkg-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.json che installerà la porta sdl2:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>.devinit.json che installerà più porte:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```