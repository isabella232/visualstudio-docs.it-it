---
title: -Deploy (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando Deploy devenv per distribuire una soluzione dopo una compilazione o una ricompilazione.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 34ad9f8da134241ce818cf37022a28fd8509b7f5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117371"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Distribuisce una soluzione dopo una compilazione o ricompilazione. Si applica solo ai progetti di codice gestito.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argomenti

- *Solutionname*

  Obbligatorio. Il percorso completo e il nome del file della soluzione.

- *SolnConfigName*

  facoltativo. Nome della configurazione di soluzione (ad esempio `Debug` o `Release`) da usare per compilare la soluzione indicata in *SolutionName*. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il nome visualizzato del progetto o un percorso relativo dalla cartella *SolutionName* al file di progetto. È anche possibile immettere il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *ProjConfigName*

  facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da usare per la compilazione del `/Project` denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se si specifica questa opzione, viene eseguito l'override dell'argomento *SolnConfigName*.

- `/Out`*OutputFilename*

  facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Commenti

Il progetto specificato deve essere un progetto di distribuzione. Se non lo è, quando il progetto compilato viene passato per la distribuzione, genererà un errore.

Racchiudere le stringhe che includono spazi tra virgolette doppie.

Le informazioni di riepilogo per le compilazioni,  inclusi gli errori, possono essere visualizzate nella finestra di comando o in qualsiasi file di log specificato con [l'opzione /Out.](out-devenv-exe.md)

## <a name="example"></a>Esempio

Questo esempio distribuisce il progetto `CSharpWinApp` usando la configurazione della build del progetto `Release` all'interno di `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
