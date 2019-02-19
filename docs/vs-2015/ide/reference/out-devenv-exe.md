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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b198732a5771ad39dab6d3797bad01e7b55c189
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54770620"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Specifica un file per archiviare e visualizzare gli errori quando si esegue, compila, ricompila o distribuisce una soluzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Argomenti  
 `FileName`  
 Obbligatorio. Percorso e nome del file per ricevere errori quando si compila un eseguibile.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un nome file che non esiste, il file viene creato automaticamente. Se il file esiste già, i risultati vengono aggiunti al contenuto del file già esistente.  
  
 Gli errori di compilazione della riga di comando vengono visualizzati nella finestra **Comando** e nella vista del generatore di soluzioni della finestra **Output**. Questa opzione è utile se si eseguono compilazioni automatiche ed è necessario visualizzare i risultati.  
  
## <a name="example"></a>Esempio  
 Questo esempio esegue `MySolution` e gli errori vengono scritti nel file `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
