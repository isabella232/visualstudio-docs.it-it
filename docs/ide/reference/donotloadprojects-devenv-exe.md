---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569855"
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

## <a name="see-also"></a>Vedere anche

- [Soluzioni filtrate in Visual Studio](../filtered-solutions.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
