---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938683"
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