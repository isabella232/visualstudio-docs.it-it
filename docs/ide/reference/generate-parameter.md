---
title: Generare un parametro - Refactoring
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare automaticamente un parametro del metodo.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d6501aca83d0a98d15b9419f98a89f2221eb45c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711662"
---
# <a name="generate-parameter"></a>Generare un parametro

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Genera automaticamente un parametro del metodo.

**Quando:** Si fa riferimento a una variabile in un metodo che non esiste nel contesto corrente e si riceve un errore. è possibile generare un parametro come correzione del codice. 

**Perché:** È possibile modificare rapidamente la firma di un metodo senza perdere il contesto.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome della variabile e premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
1. Selezionare **Generate parameter** (Genera parametro).

   ![Generare un parametro](media/generate-parameter.png) 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
