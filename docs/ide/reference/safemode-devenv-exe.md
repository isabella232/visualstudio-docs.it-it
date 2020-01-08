---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593590"
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
