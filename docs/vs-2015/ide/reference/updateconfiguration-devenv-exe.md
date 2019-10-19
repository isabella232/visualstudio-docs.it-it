---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50773821b328ea81381744bc6f32b3907cd1c5bc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657911"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Notifica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che è necessario unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e controllare se vi sono modifiche della cache MEF.

## <a name="syntax"></a>Sintassi

```
devenv /updateconfiguration
```

## <a name="remarks"></a>Osservazioni
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esegue questo comando automaticamente quando si installa un pacchetto VSIX. È consigliabile eseguire `devenv.exe /updateconfiguration` dopo l'applicazione di patch ai file in modo che [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] aggiorni la cache MEF. Ciò consente di valutare se la correzione è adeguata.

## <a name="example"></a>Esempio
 La riga di comando seguente indica a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] di unire i pacchetti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nel sistema e di controllare se vi sono modifiche della cache MEF.

```
Devenv.exe /updateconfiguration
```

## <a name="see-also"></a>Vedere anche
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [devenv opzioni della riga di comando](../../ide/reference/devenv-command-line-switches.md)
