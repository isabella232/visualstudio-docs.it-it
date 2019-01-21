---
title: -Project (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1706d8dade02bd7f247d7f2ce163955615a3b0f3
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269186"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)

Identifica un singolo progetto all'interno della configurazione della soluzione specificata da compilare, pulire, ricompilare o distribuire.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argomenti

- *SolutionName*

  Obbligatorio. Il percorso completo e il nome del file della soluzione.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obbligatorio. [Compila](build-devenv-exe.md), [pulisce](clean-devenv-exe.md), [distribuisce](deploy-devenv-exe.md) o [ridistribuisce](rebuild-devenv-exe.md) il progetto.

- *SolnConfigName*

  Facoltativo. Nome della configurazione di soluzione (ad esempio `Debug` o `Release`) applicata alla soluzione indicata in *SolutionName*. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il nome visualizzato del progetto o un percorso relativo dalla cartella *SolutionName* al file di progetto. È anche possibile immettere il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *ProjConfigName*

  Facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da applicare al `/Project` denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`).

- `/Out` *OutputFilename*

  Facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Note

- Deve essere usata come parte di un comando `devenv` `/Build`, `/Clean`, `/Rebuild` o `/Deploy`.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/Out`.

## <a name="example"></a>Esempio

Questo esempio compila il progetto `CSharpWinApp` usando la configurazione della build del progetto `Debug` all'interno di `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)