---
title: Convertire tra proprietà auto e proprietà completa
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395412"
---
# <a name="convert-between-auto-property-and-full-property"></a>Convertire tra proprietà auto e proprietà completa

Questo refactoring si applica a:

- C#

**Cosa:** Convertire tra una proprietà implementata automaticamente a una proprietà completa.

**Quando:** La logica della proprietà è stata modificata.

**Perché:** È possibile convertire manualmente tra una proprietà implementata automaticamente in una proprietà completa, tuttavia questa funzionalità eseguirà automaticamente il lavoro per l'utente. 

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sul nome della proprietà.
2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
3. Selezionare una delle due opzioni seguenti: 

    Selezionare **Converti in proprietà completa**.

   ![Convertire una proprietà automatica in proprietà completa](media/convert-auto-property-to-full-property.png) 

    Selezionare **Usa proprietà automatica**. 

    ![Convertire la proprietà completa in proprietà automaticaConvert full property to auto property](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
