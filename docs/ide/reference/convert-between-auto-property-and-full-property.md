---
title: Eseguire la conversione tra proprietà automatica e proprietà completa
description: Informazioni su come usare il menu Azioni rapide e refactoring per eseguire la conversione tra una proprietà implementata automaticamente e una proprietà completa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0e3a2f2c5ea08375a9a6596717ab43cd17fd5228
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094334"
---
# <a name="convert-between-auto-property-and-full-property"></a>Eseguire la conversione tra proprietà automatica e proprietà completa

Questo refactoring si applica a:

- C#

**Cosa:** Eseguire la conversione tra una proprietà implementata automaticamente in una proprietà completa.

**Quando:** La logica della proprietà è stata modificata.

**Perché:** È possibile eseguire manualmente la conversione tra una proprietà implementata automaticamente in una proprietà completa, ma questa funzionalità esegue automaticamente il lavoro. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sul nome della proprietà.
2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti: 

    Selezionare **Converti in proprietà completa**.

   ![Convertire una proprietà automatica in proprietà completa](media/convert-auto-property-to-full-property.png) 

    Selezionare **Usa proprietà automatica**. 

    ![Convertire la proprietà completa in proprietà automatica](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
