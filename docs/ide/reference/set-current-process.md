---
title: Imposta processo corrente
description: Informazioni sul comando Imposta processo corrente e su come imposta il processo specificato come processo attivo nel debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: c5f4aed5c44d8e3fe18ebbfdfaf2e4459bb14888608df91a9fcccd0c813ec67c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372023"
---
# <a name="set-current-process"></a>Imposta processo corrente
Imposta il processo specificato come processo attivo nel debugger.

## <a name="syntax"></a>Sintassi

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argomenti
`index`

Obbligatorio. L'indice del processo.

## <a name="remarks"></a>Commenti
Sebbene sia possibile connettersi a più processi durante il debug, nel debugger è attivo un solo processo alla volta. Per impostare il processo attivo, è possibile usare il comando `SetCurrentProcess`.

## <a name="example"></a>Esempio

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vedere anche

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
