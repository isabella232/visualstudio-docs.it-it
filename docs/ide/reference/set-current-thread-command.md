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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cedd37ece7bcc0eb79ad52cc426b07f8cb2ca57
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616564"
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