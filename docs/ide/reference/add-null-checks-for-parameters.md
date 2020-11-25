---
title: Aggiungere controlli Null per tutti i parametri
description: Informazioni su come creare e aggiungere istruzioni If al codice che controllano i valori null di tutti i parametri nullable e non controllati.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870963"
---
# <a name="add-null-checks-for-all-parameters"></a>Aggiungere controlli null per tutti i parametri 

Questo refactoring si applica a: 

- C# 

**Cosa:** Crea e aggiunge `if` istruzioni che controllano i valori null di tutti i parametri nullable, non controllati. 

**Quando:** Si desidera aggiungere rapidamente controlli null per tutti i parametri del metodo applicabili.

**Motivo:** La scrittura di controlli null per molti parametri può richiedere molto tempo e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.  

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore su qualsiasi parametro all'interno del metodo.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Azioni rapide e refactoring](media/add-null-checks-for-all-parameters.png)
   
3. Selezionare l'opzione per **aggiungere i controlli null per tutti i parametri**.

   ![Aggiungere controlli Null per tutti i parametri](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md)
