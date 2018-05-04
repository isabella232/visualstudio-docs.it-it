---
title: opzione setup devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

L'opzione /setup impone a Visual Studio l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i pacchetti VSPackage disponibili.

## <a name="syntax"></a>Sintassi

```shell
devenv /setup
```

## <a name="remarks"></a>Note

Questa opzione non accetta argomenti. Il comando `devenv /setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'opzione `/setup` non causa l'avvio di Visual Studio.

> [!NOTE]
> Per poter usare l'opzione `/setup`, è necessario eseguire `devenv` come amministratore.

## <a name="example"></a>Esempio

Questo esempio illustra l'ultimo passaggio dell'installazione di una versione di Visual Studio che include pacchetti VSPackage.

```shell
devenv /setup
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)