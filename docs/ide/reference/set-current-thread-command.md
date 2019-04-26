---
title: Comando Imposta thread corrente
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88ede32645c9fc761c476e9f4d45ddf11a7577a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934623"
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
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)