---
title: -Diff (devenv.exe)
description: Informazioni su come usare l'opzione della riga di comando Devenv Diff per confrontare due file.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: b3db029bc530cf90f48fd92901c7c55a7a0e9ae1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094087"
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

  facoltativo. Nome visualizzato del primo file.

- *TargetDisplayName*

  facoltativo. Nome visualizzato del secondo file.

## <a name="remarks"></a>Commenti

Se un'istanza dell'IDE è già aperta, il confronto dei file viene visualizzato in una scheda nell'IDE corrente.

## <a name="example"></a>Esempio

Il primo esempio confronta due file senza modificare i nomi visualizzati. Il secondo esempio confronta i file e modifica entrambi i nomi visualizzati. Il terzo e il quarto esempio confrontano i due file, ma applicano un alias solo al primo file o al secondo file.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Vedi anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
