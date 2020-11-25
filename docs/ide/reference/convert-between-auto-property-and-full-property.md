---
title: Eseguire la conversione tra proprietà automatica e proprietà completa
description: Informazioni su come usare il menu azioni rapide e refactoring per eseguire la conversione tra una proprietà implementata automaticamente e una proprietà completa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b53f337b538ff1c0aef84272eea7d9e032eb2c1d
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040836"
---
# <a name="convert-between-auto-property-and-full-property"></a>Eseguire la conversione tra proprietà automatica e proprietà completa

Questo refactoring si applica a:

- C#

**Cosa:** Eseguire la conversione tra una proprietà implementata automaticamente in una proprietà completa.

**Quando:** La logica della proprietà è stata modificata.

**Motivo:** È possibile eseguire manualmente la conversione tra una proprietà implementata automaticamente in una proprietà completa, tuttavia questa funzionalità eseguirà automaticamente il lavoro. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sul nome della proprietà.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti: 

    Selezionare **Converti in proprietà completa**.

   ![Convertire una proprietà automatica in proprietà completa](media/convert-auto-property-to-full-property.png) 

    Selezionare **Usa proprietà automatica**. 

    ![Converti proprietà completa in proprietà automatica](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
