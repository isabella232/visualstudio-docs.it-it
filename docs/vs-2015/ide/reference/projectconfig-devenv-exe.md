---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662091"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica la configurazione di compilazione di un progetto da applicare quando si compila, si pulisce, si ricompila o si distribuisce il progetto indicato nell'argomento `/project`.

## <a name="syntax"></a>Sintassi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argomenti
 /Build compila il progetto specificato da `/project` `ProjName`.

 /Clean pulisce tutti i file intermedi e le directory di output creati durante una compilazione.

 /Rebuild pulisce quindi compila il progetto specificato da `/project` `ProjName`.

 /Deploy specifica che il progetto deve essere distribuito dopo una compilazione o una ricompilazione.

 `SolnConfigName` Obbligatorio. Il nome della configurazione di soluzione da applicare alla soluzione indicata in `SolutionName`.

 `SolutionName` Obbligatorio. Il percorso completo e il nome del file della soluzione.

 /project `ProjName` Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.

 /projectconfig `ProjConfigName` Facoltativo. Il nome della configurazione della build di un progetto da applicare al `/project` denominato.

## <a name="remarks"></a>Osservazioni

- Deve essere usato specificando l'opzione `/project` come parte di un comando `devenv /build`, /`clean`, `/rebuild` o `/deploy`.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 Questo esempio compila il progetto `CSharpConsoleApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
