---
title: Aggiungere controlli Null per tutti i parametri
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782307"
---
# <a name="add-null-checks-for-all-parameters"></a>Aggiungere controlli null per tutti i parametri 

Questo refactoring si applica a: 

- C# 

**Cosa:** Crea e `if` aggiunge istruzioni che controllano la nullità di tutti i parametri nullable non controllati. 

**Quando:** Si desidera aggiungere rapidamente controlli null per tutti i parametri del metodo applicabili.

**Perché:** La scrittura di controlli null per molti parametri può richiedere molto tempo e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.  

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore su qualsiasi parametro all'interno del metodo.

2. Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.

   ![Azioni rapide e refactoring](media/add-null-checks-for-all-parameters.png)
   
3. Selezionare l'opzione **Aggiungi controlli null per tutti i parametri**.

   ![Aggiungere controlli Null per tutti i parametri](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md)
