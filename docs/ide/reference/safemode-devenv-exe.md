---
title: -SafeMode (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando devenv per la modalità provvisoria per avviare Visual Studio in modalità provvisoria, caricando solo l'ambiente e i servizi predefiniti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4d8f663ca581892ba3207acbb0271586c322bad2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039874"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Avvia Visual Studio in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.

## <a name="syntax"></a>Sintassi

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Osservazioni

Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di Visual Studio assicurando un'esecuzione stabile.

## <a name="example"></a>Esempio

L'esempio seguente avvia Visual Studio in modalità sicura.

```shell
devenv /safemode
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
