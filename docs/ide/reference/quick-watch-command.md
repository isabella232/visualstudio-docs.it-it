---
title: Comando Controllo immediato
description: Informazioni sul comando Controllo rapido e su come viene visualizzato il testo selezionato o specificato nel campo Espressione della finestra Controllo immediato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ae0717b8c4f4ffe6f3d469b21d26b794ee855dc6b25a965f2642e322892b76f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387070"
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
Visualizza il testo selezionato o specificato nel campo Espressione della finestra di dialogo [Controllo immediato](../../debugger/watch-and-quickwatch-windows.md). È possibile usare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger o i contenuti di un registro. È anche possibile modificare il valore di una variabile non costante o i contenuti di un registro.

## <a name="syntax"></a>Sintassi

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argomenti

`text`\
facoltativo. Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.

## <a name="remarks"></a>Commenti

Se `text` è omesso, il testo o la parola selezionata in corrispondenza del cursore viene aggiunta alla finestra Espressioni di controllo.

## <a name="example"></a>Esempio

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Vedere anche

- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md) (Impostare un'espressione di controllo per le variabili con le finestre Espressione di controllo e Controllo immediato in Visual Studio)
- [Visual Studio Comandi](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella di ricerca/comando](../../ide/find-command-box.md)
- [Visual Studio Alias dei comandi](../../ide/reference/visual-studio-command-aliases.md)
