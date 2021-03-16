---
description: Si è provato a assegnare un valore a questo.
title: Non è possibile assegnare a' This ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c52118ee78b7ecb7efa94dd6d86cc4fb34c7d1f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571831"
---
# <a name="cannot-assign-to-this"></a>Assegnazione a 'this' non consentita
Si è provato a assegnare un valore a **questo**. **si tratta** [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] di una parola chiave che fa riferimento a una delle seguenti operazioni:

- oggetto che attualmente esegue un metodo.

- oggetto globale se non esiste alcun metodo corrente (oppure il metodo non appartiene ad altri oggetti).

Un metodo è una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funzione che viene richiamata tramite un oggetto. All'interno di un metodo, la parola chiave **this** è un riferimento all'oggetto da cui è stato richiamato il metodo (che è l'oggetto creato richiamando il costruttore della classe con l'operatore **New** ).

All'interno di un metodo, è **possibile usarlo** per fare riferimento all'oggetto corrente, ma non è possibile assegnare un nuovo valore a **questo**.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Non tentare di assegnare a **questo**. Per accedere a una proprietà o a un metodo di un oggetto di cui è stata creata un'istanza, usare l'operatore punto (ad esempio **Circle. RADIUS**).

  > [!NOTE]
  > Non è possibile assegnare un nome a una **variabile creata** dall'utente. si tratta di una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] parola riservata.

## <a name="see-also"></a>Vedi anche

- [Questa istruzione](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/this)
- [Risoluzione dei problemi relativi agli script](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)
