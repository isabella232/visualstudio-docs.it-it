---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d438e9cea35cbf178658d8def78e264804240c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654504"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Confronta due file. Le differenze vengono visualizzate in una finestra speciale di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>argomenti

- *SourceFile*

  Obbligatorio. Percorso completo e nome del primo file da confrontare.

- *TargetFile*

  Obbligatorio. Percorso completo e nome del secondo file da confrontare.

- *SourceDisplayName*

  Parametro facoltativo. Nome visualizzato del primo file.

- *TargetDisplayName*

  Parametro facoltativo. Nome visualizzato del secondo file.

## <a name="remarks"></a>Note

Se un'istanza dell'IDE è già aperta, il confronto dei file viene visualizzato in una scheda nell'IDE corrente.

## <a name="example"></a>Esempio

Il primo esempio confronta due file senza modificare i nomi visualizzati. Il secondo esempio confronta i file e modifica entrambi i nomi visualizzati. Il terzo e il quarto esempio confrontano i due file, ma applicano un alias solo al primo file o al secondo file.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
