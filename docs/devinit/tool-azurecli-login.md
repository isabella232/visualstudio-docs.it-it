---
title: azurecli-login
description: devinit tool azurecli-login.
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
ms.openlocfilehash: 64b215912c21a405c2b2c3a0feb3720a4ab16c44
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709866"
---
# <a name="azurecli-login"></a>azurecli-login

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `azurecli-login` strumento viene usato per accedere alle risorse Azure Active Directory'interfaccia della riga di comando di [Azure.](/cli/azure/authenticate-azure-cli?preserve-view=true&view=azure-cli-latest) Questo strumento usa il comando dell'interfaccia della riga di comando di Azure: , per completare l'accesso, è necessario seguire le istruzioni `az login --use-device-code` stampate nella console.

## <a name="usage"></a>Utilizzo

Se entrambe le proprietà vengono omesse o vuote, lo strumento seguirà il [comportamento](#default-behavior) predefinito descritto di seguito.

| Nome                                             | Tipo   | Obbligatoria | valore                                                                          |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà comments facoltativa. Non usato.                                          |
| [**Input**](#input)                              | stringa | No       | Non usato. Per informazioni [dettagliate,](#input) vedere Input di seguito.                               |
| [**additionalOptions**](#additional-options)     | stringa | No       | Non usato. Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.     |

### <a name="input"></a>Input

Non usato.

### <a name="additional-options"></a>Opzioni aggiuntive

Non usato.

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello strumento è installare la versione più recente dell'interfaccia della riga di comando di `azurecli-login` Azure e aggiungerla a `PATH` .

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `azurecli-login` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-trigger-azure-login"></a>.devinit.json che attiverà l'accesso ad Azure:

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