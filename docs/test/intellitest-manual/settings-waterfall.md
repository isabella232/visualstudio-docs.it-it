---
title: Impostazioni a cascata | Strumento di test per sviluppatori Microsoft IntelliTest
description: Informazioni sulle impostazioni a cascata, che organizza le impostazioni a livello di assembly, correzione ed esplorazione.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: da67c83dc7b8eeec327dc2541e5dfde4fe60a4ac5577f34baaf57f0cecb53553
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440955"
---
# <a name="settings-waterfall"></a>Impostazioni a cascata

Il concetto di cascata delle impostazioni indica che l'utente può specificare le impostazioni a livello **di assembly,** **correzione** **ed** esplorazione:

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
