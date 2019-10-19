---
title: -Setup (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663530"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Impone a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l'unione dei metadati delle risorse che descrivono menu, barre degli strumenti e gruppi di comandi contenuti in tutti i pacchetti VSPackage disponibili.

## <a name="syntax"></a>Sintassi

```
devenv /setup
```

## <a name="remarks"></a>Osservazioni
 Questa opzione non accetta argomenti. Il comando `devenv /setup` viene in genere eseguito come ultimo passaggio del processo di installazione. L'opzione `/setup` non ha l'effetto di avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

 Per poter usare le opzioni `devenv` e [devenv](../../ide/reference/setup-devenv-exe.md) è necessario eseguire [devenv](../../ide/reference/installvstemplates-devenv-exe.md) come amministratore.

## <a name="example"></a>Esempio
 Questo esempio illustra l'ultimo passaggio dell'installazione di una versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che include pacchetti VSPackage.

```
devenv /setup
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
