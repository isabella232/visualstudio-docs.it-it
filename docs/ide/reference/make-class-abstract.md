---
title: Impostare una classe come astratta
description: Informazioni su come rendere astratta la classe dopo aver scritto un metodo astratto.
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
ms.openlocfilehash: ac3d6b9cef8d20d85049da830dfb830321faab75
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214538"
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
