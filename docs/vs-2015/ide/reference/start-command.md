---
title: Comando Avvia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a216e053a08662da5da04206c780fb4455e9ec09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663489"
---
# <a name="start-command"></a>Comando Avvia
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inizia il debug del progetto di avvio.

## <a name="syntax"></a>Sintassi

```
Debug.Start [address]
```

## <a name="arguments"></a>Argomenti
 `address` Facoltativo. Indirizzo in corrispondenza del quale il programma sospende l'esecuzione, simile a un punto di interruzione nel codice sorgente. Questo argomento è valido solo in modalità di debug.

## <a name="remarks"></a>Osservazioni
 Il comando **Avvia**, quando eseguito, esegue un'operazione RunToCursor sull'indirizzo specificato.

## <a name="example"></a>Esempio
 In questo esempio viene avviato il debugger e le eccezioni vengono ignorate.

```
>Debug.Start
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
