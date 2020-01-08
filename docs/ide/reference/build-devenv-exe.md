---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595761"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Consente di compilare una soluzione o un progetto con un file di configurazione della soluzione specificato.

## <a name="syntax"></a>Sintassi

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argomenti

- *SolutionName*

  Richiesto. Il percorso completo e il nome del file della soluzione.

- *SolnConfigName*

  Parametro facoltativo. Nome della configurazione di soluzione (ad esempio `Debug` o `Release`) da usare per compilare la soluzione indicata in *SolutionName*. Se per la soluzione sono disponibili più piattaforme, è necessario specificare anche la piattaforma, ad esempio `Debug|Win32`. Se questo argomento non viene specificato o viene specificata una stringa vuota (`""`), lo strumento usa la configurazione attiva della soluzione.

- `/Project` *ProjName*

  Parametro facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere nel file di progetto il percorso relativo dalla cartella *SolutionName*, il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.

- `/ProjectConfig` *projnameconfig*

  Parametro facoltativo. Nome della configurazione della build del progetto (ad esempio, `Debug` o `Release`) da usare per la compilazione del progetto denominato. Se è disponibile più di una piattaforma di soluzione, è necessario specificare anche la piattaforma (ad esempio, `Debug|Win32`). Se si specifica questa opzione, viene eseguito l'override dell'argomento *SolnConfigName*.

- `/Out` *OutputFileName*

  Parametro facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Note

- L'opzione `/Build` esegue la stessa funzione del comando di menu **Compila soluzione** nell'ambiente di sviluppo integrato (IDE).

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo sulle compilazioni, compresi gli errori, possono essere visualizzate nella finestra di comando o in qualsiasi file di log specificato con l'opzione `/Out`.

- L'opzione `/Build` esegue la compilazione dei soli progetti modificati dopo l'ultima compilazione. Per compilare tutti i progetti in una soluzione, usare [/rebuild](../../ide/reference/rebuild-devenv-exe.md).

- Se viene visualizzato il messaggio di errore **Configurazione progetto non valida**, assicurarsi di aver specificato la piattaforma di una soluzione o di un progetto, ad esempio `Debug|Win32`.

## <a name="example"></a>Esempio

Il comando seguente compila il progetto `CSharpWinApp` usando la configurazione della build del progetto `Debug` all'interno di `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Compilare e pulire progetti e soluzioni](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
