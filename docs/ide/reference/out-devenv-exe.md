---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47601500b0404e818f4137ced1f7a589608e9881
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227850"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Specifica un file per archiviare e visualizzare gli errori quando si [esegue](run-devenv-exe.md), [esegue e chiude](runexit-devenv-exe.md), [aggiorna](upgrade-devenv-exe.md), [compila](build-devenv-exe.md), [ricompila](rebuild-devenv-exe.md), [pulisce](clean-devenv-exe.md) o [distribuisce](deploy-devenv-exe.md) una soluzione.

## <a name="syntax"></a>Sintassi

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argomenti

- *FileName*

  Obbligatorio. Percorso e nome del file per ricevere l'output quando si compila un eseguibile.

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