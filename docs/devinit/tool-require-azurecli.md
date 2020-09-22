---
title: require-azurecli
description: per lo strumento devinit è necessario azurecli.
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
ms.openlocfilehash: ad76f82a69356f4bbd40d189fb2d8e77a839b31f
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005798"
---
# <a name="require-azurecli"></a>require-azurecli

Lo `require-azurecli` strumento viene usato per installare l' [interfaccia](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest&preserve-view=true) della riga di comando di Azure tramite l'identità del servizio gestito di Azure.

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                          |
| [**input**](#input)                              | stringa | No       | Non usato. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                               |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.     |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `require-azurecli` strumento consiste nell'installare la versione più recente dell'interfaccia della riga di comando di Azure e aggiungerla al percorso (solo Windows).

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing the Azure CLI.",
            "tool": "require-azurecli"
        }
    ]
}
```
