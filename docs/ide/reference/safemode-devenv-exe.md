---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: c2c678d7304c879cf42c24de9d83704971043676
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.

## <a name="syntax"></a>Sintassi

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Note
 Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assicurando un'esecuzione stabile.

## <a name="description"></a>Descrizione
 Nell'esempio seguente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato in modalità sicura.

## <a name="code"></a>Codice

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)