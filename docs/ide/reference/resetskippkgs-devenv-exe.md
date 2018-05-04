---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6199bf96bc631cf1018b2cb72a4d3c3cf7c703cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Cancella tutte le opzioni per ignorare il caricamento aggiunte ai pacchetti VSPackage dagli utenti che vogliono evitare di caricare i pacchetti problematici, quindi avvia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintassi

```
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Note
 La presenza di un tag SkipLoading disabilita il caricamento di un pacchetto VSPackage. La cancellazione del tag riabilita il caricamento del pacchetto VSPackage.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono cancellati tutti i tag SkipLoading.

```
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)