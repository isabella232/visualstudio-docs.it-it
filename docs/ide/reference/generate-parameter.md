---
title: Generare un parametro - Refactoring
description: Informazioni su come usare il menu azioni rapide e refactoring per generare automaticamente un parametro del metodo.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968034"
---
# <a name="generate-parameter"></a>Generare un parametro

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Genera automaticamente un parametro del metodo.

**Quando:** Si fa riferimento a una variabile in un metodo che non esiste nel contesto corrente e si riceve un errore. è possibile generare un parametro come correzione del codice. 

**Motivo:** È possibile modificare rapidamente una firma del metodo senza perdere il contesto.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome della variabile e premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
1. Selezionare **Generate parameter** (Genera parametro).

   ![Generare un parametro](media/generate-parameter.png) 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
