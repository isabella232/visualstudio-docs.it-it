---
title: Comando Imposta thread corrente
description: Informazioni sul comando Imposta thread corrente e su come imposta il thread specificato come thread corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2cb58bf8751eb4299ecede18bac83770c3a7df96
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957738"
---
# <a name="set-current-thread-command"></a>Comando Imposta thread corrente
Imposta il thread specificato come thread corrente.

## <a name="syntax"></a>Sintassi

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argomenti
`index`

Obbligatorio. Seleziona un thread in base al relativo indice.

## <a name="example"></a>Esempio

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)