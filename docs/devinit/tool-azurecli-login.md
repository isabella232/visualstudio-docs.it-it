---
title: azurecli-login
description: strumento devinit azurecli-login.
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
ms.openlocfilehash: 74c8144d9442c786bddeae78024fc4cf0d1e0d4a
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "91006043"
---
# <a name="azurecli-login"></a>azurecli-login

Lo `azurecli-login` strumento viene usato per accedere Azure Active Directory tramite l' [interfaccia](https://docs.microsoft.com/cli/azure/authenticate-azure-cli?view=azure-cli-latest&preserve-view=true)della riga di comando di Azure. Questo strumento usa il comando dell'interfaccia della riga di comando di Azure: `az login --use-device-code` per completare l'accesso, è necessario seguire le istruzioni stampate nella console.

## <a name="usage"></a>Utilizzo

Se entrambe le proprietà sono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

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

Il comportamento predefinito dello `azurecli-login` strumento consiste nell'installare la versione più recente dell'interfaccia della riga di comando di Azure e aggiungerla al percorso (solo Windows).

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger az login --use-device-code behavior.",
            "tool": "azurecli-login"
        }
    ]
}
```
