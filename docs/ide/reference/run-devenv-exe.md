---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 051462339ea25dde9c2b55394e1854c60a71dc7e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747765"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Compila ed esegue il progetto o la soluzione specificati.

## <a name="syntax"></a>Sintassi

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>argomenti

- *SolutionName*

  Percorso completo e nome del file di soluzione.

- *ProjectName*

  Percorso completo e nome del file di progetto.

- `/Out` *OutputFilename*

  Parametro facoltativo. Nome di un file a cui si vuole inviare l'output dello strumento. Se il file esiste già, lo strumento aggiunge l'output alla fine del file.

## <a name="remarks"></a>Note

Compila ed esegue il progetto o la soluzione specificati in base alle impostazioni specificate per la configurazione soluzione attiva. Questa opzione avvia l'IDE e lo mantiene attivo al termine dell'esecuzione del progetto o della soluzione.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo, compresi gli errori, possono essere visualizzate nella finestra **Comando** o in qualsiasi file di log specificato con l'opzione `/Out`.

## <a name="example"></a>Esempio

In questo esempio viene eseguita la soluzione `MySolution` usando la configurazione di distribuzione attiva.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)