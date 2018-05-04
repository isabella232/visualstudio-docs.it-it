---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 368680321f8ff8ab908e79e075a5797ba9ecd598
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Distribuisce una soluzione dopo una compilazione o ricompilazione. Si applica solo ai progetti di codice gestito.

## <a name="syntax"></a>Sintassi

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argomenti
 `SolnConfigName`

 Obbligatorio. Nome della configurazione della soluzione da usare per compilare la soluzione indicata in `SolutionName`.

 `SolutionName`

 Obbligatorio. Il percorso completo e il nome del file della soluzione.

 /project `ProjName`

 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.

 /projectconfig `ProjConfigName`

 Facoltativo. Nome della configurazione di compilazione del progetto da usare per la compilazione del `/project` denominato.

## <a name="remarks"></a>Note
 Il progetto specificato deve essere un progetto di distribuzione. Se non lo è, quando il progetto compilato viene passato per essere distribuito genererà un errore.

 Racchiudere le stringhe che includono spazi tra virgolette doppie.

 Le informazioni di riepilogo per le compilazioni, compresi gli errori, vengono visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 In questo esempio viene distribuito il progetto `CSharpConsoleApp` usando la configurazione della build del progetto `Release` all'interno della configurazione della soluzione `Release` di `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)