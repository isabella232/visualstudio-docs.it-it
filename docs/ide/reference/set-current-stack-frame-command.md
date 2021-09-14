---
title: Comando Imposta stack frame corrente
description: Informazioni sul comando Imposta stack frame corrente e su come consente di impostare un determinato stack frame.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6d003a953c411723ae8b7d52055923db21b85ba6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627119"
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

- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)