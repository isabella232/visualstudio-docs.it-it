---
title: -DoNotLoadProjects (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv doNotLoadProjects per aprire la soluzione specificata senza caricare progetti.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ab801d73fd3ae3879ca402c581520cda7df4dd8493bb0b0ed1b0a55eb69c551a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387603"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novità di Visual Studio 2019 versione 16.1**

Apre la soluzione specificata senza caricare progetti. Per altre informazioni, vedere [Soluzioni filtrate in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintassi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argomenti

*Solutionname*

Obbligatorio. Percorso completo e nome della soluzione da aprire.

## <a name="example"></a>Esempio

L'esempio apre la soluzione MySln.sln senza caricare alcun progetto.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Vedi anche

- [Soluzioni filtrate in Visual Studio](../filtered-solutions.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
