---
title: Eseguire la conversione tra proprietà automatica e proprietà completa
description: Informazioni su come usare il menu azioni rapide e refactoring per eseguire la conversione tra una proprietà implementata automaticamente e una proprietà completa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907599"
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

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
