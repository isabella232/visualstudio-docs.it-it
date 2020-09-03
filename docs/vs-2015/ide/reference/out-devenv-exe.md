---
title: -Out (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662207"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica un file per archiviare e visualizzare gli errori quando si esegue, compila, ricompila o distribuisce una soluzione.

## <a name="syntax"></a>Sintassi

```
devenv /out FileName
```

## <a name="arguments"></a>Argomenti
 `FileName` Obbligatorio. Percorso e nome del file per ricevere errori quando si compila un eseguibile.

## <a name="remarks"></a>Osservazioni
 Se viene specificato un nome file che non esiste, il file viene creato automaticamente. Se il file esiste già, i risultati vengono aggiunti al contenuto del file già esistente.

 Gli errori di compilazione della riga di comando vengono visualizzati nella finestra **Comando** e nella vista del generatore di soluzioni della finestra **Output**. Questa opzione è utile se si eseguono compilazioni automatiche ed è necessario visualizzare i risultati.

## <a name="example"></a>Esempio
 Questo esempio esegue `MySolution` e gli errori vengono scritti nel file `MyErrorLog.txt`.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
