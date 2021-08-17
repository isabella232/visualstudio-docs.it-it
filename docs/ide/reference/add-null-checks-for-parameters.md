---
title: Aggiungere controlli Null per tutti i parametri
description: Informazioni su come creare e aggiungere al codice istruzioni if che controllano la nullità di tutti i parametri nullable non verificati.
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
ms.openlocfilehash: 21891c299b6c9573af4d9e2012bfbae5c474de727d42e0f949690230d74f02c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430980"
---
# <a name="add-null-checks-for-all-parameters"></a>Aggiungere controlli null per tutti i parametri 

Questo refactoring si applica a: 

- C# 

**Cosa:** Crea e aggiunge `if` istruzioni che verificano la nullità di tutti i parametri nullable non verificati. 

**Quando:** Si vogliono aggiungere rapidamente controlli Null per tutti i parametri di metodo applicabili.

**Perché:** La scrittura di controlli Null per molti parametri può richiedere molto tempo e essere ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.  

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore su qualsiasi parametro all'interno del metodo.

2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Azioni rapide e refactoring](media/add-null-checks-for-all-parameters.png)
   
3. Selezionare l'opzione Aggiungi **controlli Null per tutti i parametri**.

   ![Aggiungere controlli Null per tutti i parametri](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Vedi anche 

- [Refactoring](../refactoring-in-visual-studio.md)
