---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda81d37be0246c1181b4d82cbd17c3119b94437
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568011"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Specifica un file per archiviare e visualizzare gli errori quando si [esegue](run-devenv-exe.md), [esegue e chiude](runexit-devenv-exe.md), [aggiorna](upgrade-devenv-exe.md), [compila](build-devenv-exe.md), [ricompila](rebuild-devenv-exe.md), [pulisce](clean-devenv-exe.md) o [distribuisce](deploy-devenv-exe.md) una soluzione.

## <a name="syntax"></a>Sintassi

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argomenti

- *FileName*

  Richiesto. Percorso e nome del file per ricevere l'output quando si compila un eseguibile.

## <a name="remarks"></a>Note

Se viene specificato un nome file inesistente, il file viene creato automaticamente. Se il file esiste già, i risultati vengono aggiunti al contenuto del file già esistente.

Gli errori di compilazione della riga di comando vengono visualizzati nella finestra di **comando** e nella visualizzazione del generatore di soluzioni della finestra **Output**. Questa opzione è utile per visualizzare i risultati delle compilazioni automatiche.

## <a name="example"></a>Esempio

Questo esempio esegue `MySolution` e gli errori vengono scritti nel file `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
