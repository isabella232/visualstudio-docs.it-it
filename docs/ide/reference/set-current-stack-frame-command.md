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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1c8d0ade87ee7759593c8a465b43439f71d50d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957751"
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