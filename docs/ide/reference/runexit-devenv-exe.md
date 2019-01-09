---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fa715c97310edc447610b0c0ae61226ab5334f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955120"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Compila ed esegue il progetto o la soluzione specificati e quindi chiude l'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argomenti
 `SolutionName`

 Obbligatorio. Percorso completo e nome del file di soluzione.

 `ProjectName`

 Obbligatorio. Percorso completo e nome del file di progetto.

## <a name="remarks"></a>Note
 Compila ed esegue il progetto o la soluzione specificati in base alle impostazioni specificate per la configurazione della soluzione attiva. Questa opzione riduce a icona l'IDE durante l'esecuzione del progetto o soluzione e chiude l'IDE al termine dell'esecuzione del progetto o soluzione.

-   Racchiudere le stringhe che includono spazi tra virgolette doppie.

-   Le informazioni di riepilogo, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.

## <a name="example"></a>Esempio
 In questo esempio la soluzione `MySolution` viene eseguita nell'IDE ridotto a icona usando la configurazione distribuzione attiva e quindi l'IDE viene chiuso.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)