---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc8b8640f73bc89b43a9ef80d6762e8b2a67c96
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655737"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Specifica la configurazione di compilazione di un progetto da applicare quando si compila, si pulisce, si ricompila o si distribuisce il progetto indicato nell'argomento `/Project`.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>argomenti

- *SolutionName*

  Obbligatorio. Il percorso completo e il nome del file della soluzione.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Obbligatorio. [Compila](build-devenv-exe.md), [pulisce](clean-devenv-exe.md), [distribuisce](deploy-devenv-exe.md) o [ridistribuisce](rebuild-devenv-exe.md) il progetto.

- *SolnConfigName*

  Parametro facoltativo. Nome della configurazione di soluzione (ad esempio `Debug` o `Release`) da applicare alla soluzione indicata in *SolutionName*. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  Parametro facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il nome visualizzato del progetto o un percorso relativo dalla cartella *SolutionName* al file di progetto. È anche possibile immettere il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *ProjConfigName*

  Parametro facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da applicare al `/Project` denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`).

- `/Out` *OutputFilename*

  Parametro facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Note

L'opzione `/ProjectConfig` deve essere usata con l'opzione `/Project` come parte di un comando `/Build`, /`Clean`, `/Deploy` o `/Rebuild`.

Racchiudere le stringhe che includono spazi tra virgolette doppie.

Le informazioni di riepilogo sulle compilazioni, compresi gli errori, possono essere visualizzate nella finestra di comando o in qualsiasi file di log specificato con l'opzione `/Out`.

## <a name="example"></a>Esempio

Il comando seguente compila il progetto `CSharpWinApp` usando la configurazione della build del progetto `Debug` all'interno di `MySolution`:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)