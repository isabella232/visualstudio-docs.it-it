---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfe0fcdb039b4c7b234f3f43e6ce5741d96f5e9c
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227447"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Confronta due file. Le differenze vengono visualizzate in una finestra speciale di Visual Studio.

## <a name="syntax"></a>Sintassi

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argomenti

- *SourceFile*

  Obbligatorio. Percorso completo e nome del primo file da confrontare.

- *TargetFile*

  Obbligatorio. Percorso completo e nome del secondo file da confrontare.

- *SourceDisplayName*

  Facoltativo. Nome visualizzato del primo file.

- *TargetDisplayName*

  Facoltativo. Nome visualizzato del secondo file.
    
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
