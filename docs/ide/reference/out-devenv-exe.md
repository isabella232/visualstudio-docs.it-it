---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f240b464ddba4e0549e3faff432685201e4560f6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985641"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Specifica un file per archiviare e visualizzare gli errori quando si esegue, compila, ricompila o distribuisce una soluzione.

## <a name="syntax"></a>Sintassi

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Argomenti
 `FileName`

 Obbligatorio. Percorso e nome del file per ricevere errori quando si compila un eseguibile.

## <a name="remarks"></a>Note
 Se viene specificato un nome file che non esiste, il file viene creato automaticamente. Se il file esiste già, i risultati vengono aggiunti al contenuto del file già esistente.

 Gli errori di compilazione della riga di comando vengono visualizzati nella finestra **Comando** e nella vista del generatore di soluzioni della finestra **Output**. Questa opzione è utile se si eseguono compilazioni automatiche ed è necessario visualizzare i risultati.

## <a name="example"></a>Esempio
 Questo esempio esegue `MySolution` e gli errori vengono scritti nel file `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)