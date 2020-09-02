---
title: Genera campo privato e proprietà dal costruttore
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283723"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Genera campo privato e proprietà dal costruttore

Questo refactoring si applica a: 

- C# 

**Cosa:** Genera un campo o una proprietà privata da un costruttore. 

**Quando:** Si desidera aggiungere e inizializzare rapidamente un campo o una proprietà privata da un costruttore.

**Motivo:** La scrittura di proprietà e campi privati può richiedere molto tempo e ripetitiva. L'uso di questo refactoring è rapido e rende il programma più stabile.

## <a name="how-to"></a>Procedure 

1. Posizionare il cursore sul nome del parametro all'interno del costruttore.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.
   
3. Selezionare poi uno dei tipi seguenti:

- **Creare e inizializzare** la **Proprietà Field o create and Initialize**.

   ![Generare un campo privato dal costruttore](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Vedere anche 

- [Refactoring](../refactoring-in-visual-studio.md)
