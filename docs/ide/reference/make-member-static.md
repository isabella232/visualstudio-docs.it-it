---
title: Rendere il membro statico
description: Informazioni su come usare il menu azioni rapide e refactoring per rendere statico un membro.
ms.custom: SEO-VS-2020
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5478e85d89d4ea44d34e0a5ae9170aaffb3836f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919453"
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
