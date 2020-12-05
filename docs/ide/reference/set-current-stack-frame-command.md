---
title: Comando Imposta stack frame corrente
description: Informazioni sul comando Imposta stack frame corrente e su come consente di impostare un particolare stack frame.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 032602744247ded5cb38d8a3ae3e1157ccbc5cee
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616603"
---
# <a name="set-current-stack-frame-command"></a>Comando Imposta stack frame corrente
Consente di impostare uno stack frame specifico.

## <a name="syntax"></a>Sintassi

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argomenti
`index`

Obbligatorio. Seleziona uno stack frame in base all'indice.

## <a name="example"></a>Esempio

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)