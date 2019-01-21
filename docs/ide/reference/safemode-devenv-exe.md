---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 092cc1fc3267113e862646b7572e9091b8f6ddef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227200"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Avvia Visual Studio in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.

## <a name="syntax"></a>Sintassi

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Note

Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di Visual Studio assicurando un'esecuzione stabile.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio in modalità sicura.

```shell
devenv /safemode
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)