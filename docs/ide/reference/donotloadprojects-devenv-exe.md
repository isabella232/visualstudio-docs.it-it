---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654503"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novità di Visual Studio 2019 versione 16.1**

Apre la soluzione specificata senza caricare progetti. Per altre informazioni, vedere [Soluzioni filtrate in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintassi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>argomenti

*SolutionName*

Obbligatorio. Percorso completo e nome della soluzione da aprire.

## <a name="example"></a>Esempio

L'esempio apre la soluzione MySln.sln senza caricare alcun progetto.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Vedere anche

- [Soluzioni filtrate in Visual Studio](../filtered-solutions.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
