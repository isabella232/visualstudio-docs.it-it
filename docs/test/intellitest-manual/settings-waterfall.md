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
ms.openlocfilehash: 2ca1cdcc1da97f8fa0d5def89e4f437607b36dd9
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668755"
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

Pubblicare idee e richieste di funzionalità nella [community degli sviluppatori](https://aka.ms/feedback/suggest?space=8).
