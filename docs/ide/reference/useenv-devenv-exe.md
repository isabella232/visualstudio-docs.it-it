---
title: -UseEnv (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c48e9f22322cd5ebebeff0d987c32d369f98d03
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Avvia Visual Studio e carica le variabili di ambiente nella finestra di dialogo **Directory di VC++**.

> [!NOTE]
> Questa opzione viene installata con il carico di lavoro **Sviluppo di applicazioni desktop con C++**.

## <a name="syntax"></a>Sintassi

```shell
Devenv /useenv
```

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio e carica le variabili di ambiente nella finestra di dialogo **Directory di VC++**.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Vedere anche

* [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)