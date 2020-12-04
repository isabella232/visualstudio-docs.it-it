---
title: Rendere il membro statico
description: Informazioni su come usare il menu azioni rapide e refactoring per rendere statico un membro.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e663d59f47728bc4a7c84290ee0e89ae453f23ae
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2020
ms.locfileid: "96561019"
---
# <a name="make-member-static"></a>Rendere il membro statico

Questo refactoring si applica a:

- C#

**Cosa:** Rendere statico un membro.

**Quando:** Si vuole che un membro non statico sia statico.

**Motivo:** I membri statici migliorano la leggibilità: sapere che il codice specifico è isolato rende più semplice comprendere, rileggere e riutilizzare. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento sul nome del membro.

2. Premere **CTRL** + **.** (periodo) per attivare il menu **azioni rapide e refactoring** .

   ![Rendere il membro statico](media/make-member-static.png)

3. Selezionare **Imposta come statici**.

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
