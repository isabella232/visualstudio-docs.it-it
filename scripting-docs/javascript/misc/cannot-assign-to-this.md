---
title: Non è possibile assegnare a' This ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 73baa77cc63e3a43ac30e70f66081bbc7ade3020
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572355"
---
# <a name="cannot-assign-to-this"></a>Assegnazione a 'this' non consentita
Si è provato a assegnare un valore a **questo**. **si tratta di** una parola chiave [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che fa riferimento a una delle seguenti operazioni:

- oggetto che attualmente esegue un metodo.

- oggetto globale se non esiste alcun metodo corrente (oppure il metodo non appartiene ad altri oggetti).

Un metodo è una funzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] richiamata tramite un oggetto. All'interno di un metodo, la parola chiave **this** è un riferimento all'oggetto da cui è stato richiamato il metodo (che è l'oggetto creato richiamando il costruttore della classe con l'operatore **New** ).

All'interno di un metodo, è **possibile usarlo** per fare riferimento all'oggetto corrente, ma non è possibile assegnare un nuovo valore a **questo**.

## <a name="to-correct-this-error"></a>Per correggere l'errore

- Non tentare di assegnare a **questo**. Per accedere a una proprietà o a un metodo di un oggetto di cui è stata creata un'istanza, usare l'operatore punto (ad esempio **Circle. RADIUS**).

  > [!NOTE]
  > Non è possibile assegnare un nome a una **variabile creata**dall'utente. si tratta di una parola [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] riservata.

## <a name="see-also"></a>Vedere anche

- [Istruzione this](../../javascript/reference/this-statement-javascript.md)
- [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)