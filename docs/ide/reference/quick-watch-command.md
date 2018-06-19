---
title: Comando Controllo immediato
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce3c95591809b847141dde07b2a770d9b4597a5f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703957"
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
Visualizza il testo selezionato o specificato nel campo Espressione della finestra di dialogo [Controllo immediato](../../debugger/watch-and-quickwatch-windows.md). È possibile usare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger o i contenuti di un registro. È anche possibile modificare il valore di una variabile non costante o i contenuti di un registro.

## <a name="syntax"></a>Sintassi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argomenti
 `text`

 Facoltativo. Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.

## <a name="remarks"></a>Note
 Se `text` è omesso, il testo o la parola selezionata in corrispondenza del cursore viene aggiunta alla finestra Espressioni di controllo.

## <a name="example"></a>Esempio

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Vedere anche

- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md) (Impostare un'espressione di controllo per le variabili con le finestre Espressione di controllo e Controllo immediato in Visual Studio)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)