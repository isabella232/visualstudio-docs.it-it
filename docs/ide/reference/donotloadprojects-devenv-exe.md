---
title: -DoNotLoadProjects (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando DoNotLoadProjects devenv per aprire la soluzione specificata senza caricare alcun progetto.
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
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907588"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novità di Visual Studio 2019 versione 16.1**

Apre la soluzione specificata senza caricare progetti. Per altre informazioni, vedere [Soluzioni filtrate in Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintassi

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argomenti

*NomeSoluzione*

Obbligatorio. Percorso completo e nome della soluzione da aprire.

## <a name="example"></a>Esempio

L'esempio apre la soluzione MySln.sln senza caricare alcun progetto.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Vedi anche

- [Soluzioni filtrate in Visual Studio](../filtered-solutions.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
