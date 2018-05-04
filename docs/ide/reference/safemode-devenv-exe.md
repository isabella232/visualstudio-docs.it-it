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
ms.openlocfilehash: eaf137b699b7a02a0ee79099e937767262fce4e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modalità sicura caricando soltanto l'ambiente e i servizi predefiniti.

## <a name="syntax"></a>Sintassi

```
devenv /SafeMode
```

## <a name="remarks"></a>Note
 Questa opzione impedisce il caricamento di tutti i pacchetti VSPackage di terze parti all'avvio di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assicurando un'esecuzione stabile.

## <a name="description"></a>Descrizione
 Nell'esempio seguente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene avviato in modalità sicura.

## <a name="code"></a>Codice

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)