---
title: Comando Controllo immediato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da9ba9572e121a9eba74cd8d624789032f1bb4a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665661"
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza il testo selezionato o specificato nel campo Espressione della [finestra di dialogo Controllo immediato](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). È possibile usare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger o i contenuti di un registro. È anche possibile modificare il valore di una variabile non costante o i contenuti di un registro.

## <a name="syntax"></a>Sintassi

```
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argomenti
 `text` Facoltativo. Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.

## <a name="remarks"></a>Osservazioni
 Se `text` è omesso, il testo o la parola selezionata in corrispondenza del cursore viene aggiunta alla finestra Espressioni di controllo.

## <a name="example"></a>Esempio

```
>Debug.QuickWatch
```

## <a name="see-also"></a>Vedere anche
 [Procedura: utilizzare la finestra di dialogo controllo immediato finestra di dialogo comandi di](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando casella](../../ide/find-command-box.md) di comando [Visual Studio alias](../../ide/reference/visual-studio-command-aliases.md)
