---
title: -Run (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e10b12729ed8f547c2658c0f4ce6ece84a12dbe
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Compila ed esegue il progetto o la soluzione specificati.

## <a name="syntax"></a>Sintassi

```cmd
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti
 `SolutionName`

 Obbligatorio. Percorso completo e nome del file di soluzione.

 `ProjectName`

 Obbligatorio. Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Note
 Compila ed esegue il progetto o la soluzione specificati in base alle impostazioni specificate per la configurazione della soluzione attiva. Questa opzione avvia l'ambiente di sviluppo integrato (IDE) e lo mantiene attivo al termine dell'esecuzione del progetto o della soluzione.

-   Racchiudere le stringhe che includono spazi tra virgolette doppie.

-   Le informazioni di riepilogo, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 In questo esempio viene eseguita la soluzione `MySolution` usando la configurazione di distribuzione attiva.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)