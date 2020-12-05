---
title: Genera campo privato e proprietà dal costruttore
description: Informazioni su come usare il menu azioni rapide e refactoring per generare un campo o una proprietà privata da un costruttore.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617461"
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
