---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083938"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novità di Visual Studio 2019 versione 16.1**

Apre la soluzione specificata senza caricare progetti. Per altre informazioni, vedere [Soluzioni filtrate in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintassi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argomenti

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
