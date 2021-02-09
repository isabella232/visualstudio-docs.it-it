---
title: Impostare una classe come astratta
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7b44c8331c10bc0cf2f87e19094a77c0cbec251a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919424"
---
# <a name="make-class-abstract"></a>Impostare una classe come astratta

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Effettuare il refactoring astratto della classe.

**Quando:** Si scrive un metodo astratto in una classe non astratta.

**Motivo:**  Una correzione del codice per rendere astratta una classe dopo la scrittura di un metodo astratto consente di risparmiare tempo.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore sul metodo astratto.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **make Class ' abstract '**.

    ![Impostare una classe come astratta](media/make-class-abstract.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
