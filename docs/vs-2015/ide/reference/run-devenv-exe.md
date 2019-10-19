---
title: -Run (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665516"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Compila ed esegue il progetto o la soluzione specificati.

## <a name="syntax"></a>Sintassi

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti
 `SolutionName` Obbligatorio. Percorso completo e nome del file di soluzione.

 `ProjectName` Obbligatorio. Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Osservazioni
 Compila ed esegue il progetto o la soluzione specificati in base alle impostazioni specificate per la configurazione della soluzione attiva. Questa opzione avvia l'ambiente di sviluppo integrato (IDE) e lo mantiene attivo al termine dell'esecuzione del progetto o della soluzione.

- Racchiudere le stringhe che includono spazi tra virgolette doppie.

- Le informazioni di riepilogo, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 In questo esempio viene eseguita la soluzione `MySolution` usando la configurazione di distribuzione attiva.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md) [/runexit (devenv. exe)](../../ide/reference/runexit-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
