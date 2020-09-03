---
title: -ResetSkipPkgs (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 207ceb92d84c2186aeec49c205d8d32f4d7aa969
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665570"
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cancella tutte le opzioni per ignorare il caricamento aggiunte ai pacchetti VSPackage dagli utenti che vogliono evitare di caricare i pacchetti problematici, quindi avvia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Sintassi

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Osservazioni
 La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag riabilita il caricamento del pacchetto VSPackage.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono cancellati tutti i tag SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
