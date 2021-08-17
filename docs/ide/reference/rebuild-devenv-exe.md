---
title: -Rebuild (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando Rebuild devenv per pulire e quindi compilare la configurazione della soluzione specificata.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6a3ef4a0394f62e214865e89f08d6d65771954e8724686db27a76ded978d7b46
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400114"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Pulisce e quindi compila la configurazione della soluzione specificata.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argomenti

- *Solutionname*

  Obbligatorio. Il percorso completo e il nome del file della soluzione.

- *SolnConfigName*

  facoltativo. Nome della configurazione della soluzione (ad esempio, `Debug` o `Release`) da usare per ricompilare la soluzione indicata in *SolutionName*. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il nome visualizzato del progetto o un percorso relativo dalla cartella *SolutionName* al file di progetto. È anche possibile immettere il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *ProjConfigName*

  facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da usare per la ricompilazione del `/Project` denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se si specifica questa opzione, viene eseguito l'override dell'argomento *SolnConfigName*.

- `/Out`*OutputFilename*

  facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Commenti

- Questa opzione esegue la stessa operazione del comando di menu **Ricompila soluzione** all'interno dell'IDE.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo per le operazioni di pulizia e compilazione, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione [/Out](out-devenv-exe.md).

## <a name="example"></a>Esempio

Questo esempio pulisce e ricompila il progetto `CSharpWinApp` usando la configurazione della build del progetto `Debug` all'interno di `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
