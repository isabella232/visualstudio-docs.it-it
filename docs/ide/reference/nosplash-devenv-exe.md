---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1e8118faa743398271fb282a2603aab5fcd76b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937955"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Impedisce la visualizzazione della schermata iniziale.

## <a name="syntax"></a>Sintassi

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argomenti

- *File1*

  Facoltativo. File da aprire in un'istanza esistente di Visual Studio. Se non esiste alcuna istanza di Visual Studio, viene creata una nuova istanza con un layout di finestra semplificato e lo strumento apre *File1* nella nuova istanza.

- *FileN*

  Facoltativo. Uno o più file aggiuntivi da aprire nell'istanza esistente di Visual Studio.

## <a name="remarks"></a>Note

Questa opzione nasconde la schermata iniziale. Se si omette questa opzione, la schermata iniziale viene visualizzata. Se si vuole esaminare ulteriormente la schermata iniziale (ad esempio, per controllare l'icona del prodotto VSPackage), usare l'opzione [/Splash](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

L'opzione `/NoSplash` può essere combinata con altre opzioni, ad esempio [/Run](run-devenv-exe.md) oppure [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Esempio

Tutti e tre gli esempi aprono l'IDE senza visualizzare la schermata iniziale. Il secondo esempio compila inoltre la soluzione specificata ed esegue l'eseguibile compilato. Il terzo esempio apre l'eseguibile specificato per il debug nell'IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [Opzioni della riga di comando devenv per lo sviluppo di pacchetti VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
