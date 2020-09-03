---
title: -Project (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662116"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Identifica un singolo progetto all'interno della configurazione della soluzione specificata da compilare, pulire, ricompilare o distribuire.

## <a name="syntax"></a>Sintassi

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argomenti
 /Build compila il progetto specificato da `/project` `ProjName` .

 /Clean pulisce tutti i file intermedi e le directory di output creati durante una compilazione.

 /Rebuild pulisce quindi compila il progetto specificato da `/project` `ProjName` .

 /Deploy specifica che il progetto deve essere distribuito dopo una compilazione o una ricompilazione.

 `SolnConfigName` Obbligatorio. Il nome della configurazione di soluzione da applicare alla soluzione indicata in `SolutionName`.

 `SolutionName` Obbligatorio. Il percorso completo e il nome del file della soluzione.

 /project `ProjName` Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.

 /projectconfig `ProjConfigName` Facoltativo. Il nome della configurazione della build di un progetto da applicare al `/project` denominato.

## <a name="remarks"></a>Osservazioni

- Deve essere usata come parte di un comando `devenv /build`, /`clean`, `/rebuild` o `/deploy`.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo sulle compilazioni, compresi gli errori, possono essere visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 Questo esempio compila il progetto `CSharpConsoleApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
