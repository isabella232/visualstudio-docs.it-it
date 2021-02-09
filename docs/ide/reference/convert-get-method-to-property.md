---
title: Convertire il metodo Get in o da una proprietà
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un metodo Get (e facoltativamente il metodo set) in una proprietà.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d86a9c42fbd1c54e7bef409cc6d61d9aca751436
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919653"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refactoring per convertire il metodo Get in proprietà o una proprietà in metodo Get

Questi refactoring si applicano a:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Convertire il metodo Get in proprietà

**Cosa:** consente di convertire un metodo Get in una proprietà (e facoltativamente il metodo Set).

**Quando:** si ha un metodo Get che non contiene alcuna logica.

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL** + **.** per attivare il menu **azioni rapide e refactoring** e selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse sul codice, scegliere il menu **azioni rapide e refactoring** e selezionare **Sostituisci metodo con la proprietà** dal popup della finestra di anteprima.

1. (Facoltativo) Se si dispone di un metodo Set, è anche possibile convertire il metodo Set in questo momento selezionando **Sostituisci metodo Get e metodo Set con la proprietà**.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

Esempio:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertire una proprietà in un metodo Get

**Cosa:** consente di convertire una proprietà in un metodo Get

**Quando:** è presente una proprietà con maggiori requisiti rispetto all'impostazione e al recupero immediati di un valore

### <a name="how-to"></a>Procedure

1. Posizionare il cursore nel nome del metodo Get.

1. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.
   - **Mouse**
      - fare clic con il pulsante destro del mouse sul codice e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Sostituisci proprietà con metodi** dal popup della finestra di anteprima.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **INVIO** o fare clic sulla correzione nel menu. Verrà eseguito il commit delle modifiche.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
