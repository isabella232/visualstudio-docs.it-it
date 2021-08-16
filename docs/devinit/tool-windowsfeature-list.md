---
title: windowsfeature-list
description: devinit tool windowsfeature-list.
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
ms.openlocfilehash: 79190ef76e0a3693dca7410fa06b55e0f3cb8768cdb60d0804730b5e1a2c6388
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378244"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `windowsfeature-list` strumento viene usato per elencare lo stato di abilitazione/disabilitazione di tutte Windows funzionalità.

| Nome                                             | Tipo   | Obbligatoria | valore                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.      |
| [**Input**](#input)                              | stringa | No       | Non usato. Ignorato.                         |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Ignorato.                         |

### <a name="input"></a>Input

Non usato. Ignorato.

#### <a name="additional-options"></a>Opzioni aggiuntive

Non usato. Ignorato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento `windowsfeature-list` è elencare lo stato di abilitazione/disabilitazione di tutte Windows funzionalità.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `windowsfeature-list` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.jsin verrà elencato lo stato di tutte le Windows seguenti:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
