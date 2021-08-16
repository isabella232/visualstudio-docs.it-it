---
title: require-azurecli
description: devinit tool require-azurecli.
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
ms.openlocfilehash: 84b6506f2aa9c284a97521bf865572773f61908b2def3ef17644cc20234ac037
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390557"
---
# <a name="require-azurecli"></a>require-azurecli

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è incentrata sull'evoluzione delle esperienze per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di Visual Studio di lavoro. Come parte di questo `devinit` e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community per sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `require-azurecli` strumento viene usato per installare l'interfaccia della riga di comando di [Azure](/cli/azure/?view=azure-cli-latest&preserve-view=true) tramite l'interfaccia della riga di comando di Azure.

## <a name="usage"></a>Utilizzo

Se `input` entrambe le proprietà e vengono omesse o vuote, lo strumento seguirà `additionalOptions` il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                          |
| [**Input**](#input)                              | stringa | No       | Non usato. Per [informazioni dettagliate,](#input) vedere Input di seguito.                               |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.     |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è installare la versione più recente dell'interfaccia della riga di comando di `require-azurecli` Azure e aggiungerla a `PATH` .

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `require-azurecli` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-azure-cli"></a>.devinit.jsin che installerà l'interfaccia della riga di comando di Azure:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-azurecli"
        }
    ]
}
```