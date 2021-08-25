---
title: Aggiungere controlli Null per tutti i parametri
description: Informazioni su come creare e aggiungere istruzioni if al codice che controllano la nullità di tutti i parametri nullable e non controllati.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a53f31b0cdd30585b6f1c5e662787d1d8195187
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785962"
---
# <a name="add-null-checks-for-all-parameters"></a>Aggiungere controlli null per tutti i parametri 

Questo refactoring si applica a: 

- C# 

**Cosa:** Crea e aggiunge `if` istruzioni che verificano la nullità di tutti i parametri nullable non verificati. 

**Quando:** Si vuole aggiungere rapidamente controlli Null per tutti i parametri di metodo applicabili.

**Perché:** La scrittura di controlli Null per molti parametri può richiedere molto tempo e essere ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.  

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore su qualsiasi parametro all'interno del metodo.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Azioni rapide e refactoring](media/add-null-checks-for-all-parameters.png)
   
3. Selezionare l'opzione Aggiungi **controlli Null per tutti i parametri**.

   ![Aggiungere controlli Null per tutti i parametri](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vedi anche 

- [Refactoring](../refactoring-in-visual-studio.md)
