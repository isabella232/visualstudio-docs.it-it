---
title: Impostare una classe come astratta
description: Informazioni su come rendere la classe astratta dopo la scrittura di un metodo astratto.
ms.date: 11/03/2020
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
ms.openlocfilehash: 767a81ae1957a7a3c2865bef060f5f0016e7a7c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101089"
---
# <a name="make-class-abstract"></a>Impostare una classe come astratta

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Rendere il refactoring astratto della classe.

**Quando:** Si scrive un metodo astratto in una classe che non è astratta.

**Perché:**  La correzione di codice per rendere astratta una classe dopo la scrittura di un metodo astratto consente di risparmiare tempo.

## <a name="how-to"></a>Procedure

1. Posizionare il punto di caret sul metodo astratto.

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **Rendi classe 'astratta'.**

    ![Impostare una classe come astratta](media/make-class-abstract.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
