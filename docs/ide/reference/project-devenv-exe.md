---
title: -Project (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv Project per identificare un singolo progetto all'interno della configurazione di soluzione specificata per compilare, pulire, ricompilare o distribuire il progetto.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- Project Devenv switch (/Project)
- Devenv, /Project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5be70c47759831c452e513ab2a4d4432840c1022
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628577"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifica un singolo progetto all'interno della configurazione della soluzione specificata da compilare, pulire, ricompilare o distribuire.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argomenti

- *Solutionname*

  Obbligatorio. Il percorso completo e il nome del file della soluzione.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obbligatorio. [Compila](build-devenv-exe.md), [pulisce](clean-devenv-exe.md), [distribuisce](deploy-devenv-exe.md) o [ridistribuisce](rebuild-devenv-exe.md) il progetto.

- *SolnConfigName*

  facoltativo. Nome della configurazione di soluzione (ad esempio `Debug` o `Release`) applicata alla soluzione indicata in *SolutionName*. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il nome visualizzato del progetto o un percorso relativo dalla cartella *SolutionName* al file di progetto. È anche possibile immettere il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *ProjConfigName*

  facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da applicare al `/Project` denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`).

- `/Out`*OutputFilename*

  facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Commenti

- Deve essere usato parte di `devenv` `/Build` un comando , , `/Clean` o `/Rebuild` `/Deploy` .

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo sulle compilazioni, compresi gli errori, possono essere visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/Out`.

## <a name="example"></a>Esempio

Questo esempio compila il progetto `CSharpWinApp` usando la configurazione della build del progetto `Debug` all'interno di `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
