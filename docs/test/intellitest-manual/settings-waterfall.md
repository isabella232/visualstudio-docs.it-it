---
title: Impostazioni a cascata | Strumento di test per sviluppatori Microsoft IntelliTest
description: Informazioni sulle impostazioni della cascata, che organizza le impostazioni a livello di assembly, di fixture e di esplorazione.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bdb053218b65924abfa64053a8a3c7e9e0543d49
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329510"
---
# <a name="settings-waterfall"></a>Impostazioni a cascata

Il concetto di impostazioni a cascata significa che l'utente può specificare le impostazioni a livello di **assembly**, di **fixture** e di **esplorazione** :

* Assembly: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Fixture: [PexClass](attribute-glossary.md#pexclass)
* Esplorazione: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Le impostazioni specificate a livello di **assembly** hanno effetto su tutte le fixture e le esplorazioni sotto tale assembly. Le impostazioni specificate a livello di **fixture** hanno effetto su tutte le esplorazioni sotto tale fixture. Le impostazioni figlio hanno la precedenza&mdash; se un'impostazione è definita sia a livello di **assembly** che a livello di **fixture** viene usata l'impostazione definita a livello di **fixture**.

Si noti che alcune impostazioni sono specifiche per il livello di **assembly** o il livello di **fixture**.

**Esempio**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Per eventuali commenti,

Pubblicare idee e richieste di funzionalità nella [community degli sviluppatori](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).
