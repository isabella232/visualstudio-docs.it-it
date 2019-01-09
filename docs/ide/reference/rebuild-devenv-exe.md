---
title: -Rebuild (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 782a0864c692d8c50932f41077762c994f24eeae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985683"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Pulisce e quindi compila la configurazione della soluzione specificata.

## <a name="syntax"></a>Sintassi

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argomenti
 `SolnConfigName`

 Obbligatorio. Nome della configurazione della soluzione da usare per ricompilare la soluzione indicata in `SolutionName`.

 `SolutionName`

 Obbligatorio. Il percorso completo e il nome del file della soluzione.

 /project `ProjName`

 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.

 /projectconfig `ProjConfigName`

 Facoltativo. Nome della configurazione di compilazione del progetto da usare per la ricompilazione dell'elemento `/project` denominato.

## <a name="remarks"></a>Note

-   Questa opzione esegue la stessa funzione del comando di menu **Ricompila soluzione** nell'ambiente di sviluppo integrato (IDE).

-   Racchiudere le stringhe che includono spazi tra virgolette doppie.

-   Le informazioni di riepilogo sulle operazioni di pulizia e compilazione, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 Questo esempio pulisce e ricompila il progetto `CSharpWinApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)