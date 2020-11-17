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
ms.openlocfilehash: 304c7b12e3b290c3e47857877b050b18873e3934
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672311"
---
# <a name="azurecli-login"></a>azurecli-login

Lo `azurecli-login` strumento viene usato per accedere Azure Active Directory tramite l' [interfaccia](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest)della riga di comando di Azure. Questo strumento usa il comando dell'interfaccia della riga di comando di Azure: `az login --use-device-code` per completare l'accesso, è necessario seguire le istruzioni stampate nella console.

## <a name="usage"></a>Utilizzo

Se entrambe le proprietà sono omesse o vuote, lo strumento seguirà il comportamento [predefinito](#default-behavior) descritto di seguito.

| Nome                                             | Type   | Obbligatoria | valore                                                                          |
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
Di seguito è riportato un esempio di come eseguire `azurecli-login` usando un `.devinit.json` . 

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.json che attiverà Azure login:

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "azurecli-login"
        }
    ]
}
```