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
ms.openlocfilehash: 9456c81ff93eed6872bafbc7427e862a705c17072bcb3ae5a7e32c97d1685805
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387336"
---
# <a name="make-member-static"></a>Rendere il membro statico

Questo refactoring si applica a:

- C#

**Cosa:** Rendere statico un membro.

**Quando:** Si vuole che un membro non statico sia statico.

**Perché:** I membri statici migliorano la leggibilità: sapere che il codice specifico è isolato semplifica la comprensione, la rilettura e il riutilizzo. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sul nome del membro.

2. Premere  + **CTRL+ .** (punto) per attivare il menu **Azioni rapide e refactoring.**

   ![Rendere il membro statico](media/make-member-static.png)

3. Selezionare **Imposta come statici**.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
