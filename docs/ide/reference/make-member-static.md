---
title: Rendere il membro statico
description: Informazioni su come usare il menu Azioni rapide e refactoring per rendere statico un membro.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 215004e6de9cad6988707c5584ba1ff33663396d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151314"
---
# <a name="make-member-static"></a>Rendere il membro statico

Questo refactoring si applica a:

- C#

**Cosa:** Rendere statico un membro.

**Quando:** Si vuole che un membro non statico sia statico.

**Perché:** I membri statici migliorano la leggibilità: sapere che il codice specifico è isolato semplifica la comprensione, la rilettura e il riutilizzo. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di controllo sul nome del membro.

2. Premere  + **CTRL.** (punto) per attivare il menu **Azioni rapide e refactoring.**

   ![Rendere il membro statico](media/make-member-static.png)

3. Selezionare **Imposta come statici**.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
