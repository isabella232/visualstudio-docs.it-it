---
title: Choco-install
description: strumento devinit Choco-install per installare i pacchetti di cioccolato.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 0ad4c5c772ac9028ec369fe7cc63e1a2f7af6931
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810165"
---
# <a name="choco-install"></a>Choco-install

Lo `choco-install` strumento può essere usato per installare e aggiornare i pacchetti di [cioccolato](https://chocolatey.org/) .

## <a name="usage"></a>Utilizzo

Se entrambe le `input` `additionalOptions` proprietà e vengono omesse o vuote, lo strumento non eseguirà alcuna operazione.

| Nome                                             | Type   | Obbligatoria | valore                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **Commenti**                                     | stringa | No       | Proprietà commenti facoltativi. Non usato.                                                                          |
| [**input**](#input)                              | stringa | No       | Pacchetto da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                                                 |
| [**additionalOptions**](#additional-options)     | stringa | No       | Opzioni aggiuntive da passare allo strumento. Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.       |

### <a name="input"></a>Input

La `input` proprietà viene utilizzata per specificare il nome del pacchetto da installare, ad esempio ' MongoDB ', oppure il percorso di un file di configurazione con i formati seguenti _packages.config_, _NuSpec_e _. nupkg_. Il valore di `input` verrà accodato a un `choco install` comando (ad esempio `choco install mongodb` ) insieme a eventuali argomenti specifici di [`additionalOptions`](#additional-options) e alle `choco` opzioni predefinite (definite di [seguito](#built-in-options)). I pacchetti sono disponibili nella [raccolta di pacchetti di cioccolato](https://chocolatey.org/packages). Quando si usa un file di configurazione, ad esempio, è possibile passare il percorso del file nella `input` proprietà `"input":"packages.config"` .

### <a name="additional-options"></a>Opzioni aggiuntive

Altre opzioni di configurazione possono essere passate come valore di `additionalOptions` . Questi argomenti sono il pass-through diretto agli argomenti utilizzati da [`choco install`](https://chocolatey.org/docs/commands-install) e sono definiti nella documentazione di cioccolato.

### <a name="built-in-options"></a>Opzioni predefinite

Lo `choco-install` strumento imposta un numero di `choco` argomenti della riga di comando per garantire che sia `choco` possibile eseguire l'intestazione. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella [documentazione di cioccolato](https://chocolatey.org/docs/).

| Nome                  | Descrizione                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Sì**             | Conferma tutti i prompt: sceglie una risposta affermativa anziché richiedere. Implica `--accept-license.` |
| **--No-Progress**     | Non visualizzare lo stato di avanzamento: le percentuali di avanzamento non verranno visualizzate.                                         |
| **--Skip-PowerShell** | Ignorare PowerShell-chocolateyInstall.ps1 non verrà eseguito.                                              |

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing packages listed in a packages.config file.",
            "tool": "choco-install",
            "input": "packages.config",
        },
        {
            "comments": "Example that will install the package 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb"
        },
        {
            "comments": "Example that will install the '4.2.7' version of 'mongodb'.",
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
