---
title: Comando Go To | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661207"
---
# <a name="go-to-command"></a>Comando Vai a
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sposta il cursore sulla riga specificata.

## <a name="syntax"></a>Sintassi

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argomenti
 `linenumber` Facoltativo. Valore integer che rappresenta il numero della riga a cui passare.

## <a name="remarks"></a>Osservazioni
 La numerazione delle righe inizia da uno. Se il valore di `linenumber` è minore di uno, viene visualizzata la prima riga. Se il valore di `linenumber` è maggiore del numero dell'ultima riga, viene visualizzata l'ultima riga.

 Se non viene specificato alcun un valore per `linenumber`, viene visualizzata la finestra di dialogo **Vai alla riga**.

 L'alias per questo comando è GoToLn.

## <a name="example"></a>Esempio

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
