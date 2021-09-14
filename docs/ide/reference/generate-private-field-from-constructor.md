---
title: Generare un campo privato e una proprietà dal costruttore
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare un campo privato o una proprietà da un costruttore.
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 499398f40387ee8c5497ca32e7d3f0f56e44d788
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711651"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generare un campo privato e una proprietà dal costruttore

Questo refactoring si applica a: 

- C# 

**Cosa:** Generare un campo o una proprietà privata da un costruttore. 

**Quando:** Si vuole aggiungere e inizializzare rapidamente un campo privato o una proprietà da un costruttore.

**Perché:** La scrittura di proprietà e campi privati può richiedere molto tempo e essere ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore sul nome del parametro all'interno del costruttore.

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.
   
3. Selezionare poi uno dei tipi seguenti:

- **Creare e inizializzare il campo** o **creare e inizializzare la proprietà**.

   ![Generare un campo privato dal costruttore](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vedi anche 

- [Refactoring](../refactoring-in-visual-studio.md)
