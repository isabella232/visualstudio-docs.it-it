---
title: Implementare un'interfaccia
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare immediatamente il codice necessario per implementare un'interfaccia.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 9f5e067021e13f0a59c3b45882b204de04167559e39977446aeb779f6b4bf7e8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447696"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementare un'interfaccia in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice necessario per implementare un'interfaccia.

**Quando:** si vuole ereditare da un'interfaccia.

**Perché:** è possibile implementare manualmente tutte le interfacce, una alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato aggiunto un riferimento a un'interfaccia, ma che non sono stati implementati tutti i membri obbligatori.

   - C#:

       ![Codice evidenziato C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/interface-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina di errore](media/error-bulb.png) visualizzata.
      - Fare clic sull'icona ![lampadina di errore](media/error-bulb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

3. Scegliere **Implementa interfaccia** dal menu a discesa.

   ![Anteprima di Implementa interfaccia](media/interface-preview-cs.png)

   > [!TIP]
   > - Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.
   > - Usare i collegamenti **Documento**, **Progetto** e **Soluzione** nella parte inferiore della finestra di anteprima per creare le firme dei metodi appropriate per più classi che implementano l'interfaccia.

   Le firme del metodo dell'interfaccia vengono create e sono pronte per l'implementazione.

   - C#:

       ![Risultato di implementazione dell'interfaccia C#](media/interface-result-cs.png)

   - Visual Basic:

       ![Risultato di implementazione dell'interfaccia VB](media/interface-result-vb.png)

   > [!TIP]
   > (Solo C#) Usare l'opzione **Implementa l'interfaccia in modo esplicito** per anteporre a ogni metodo generato il nome dell'interfaccia per evitare conflitti di nome.
   >
   > ![Risultato dell'implementazione dell'interfaccia in modo esplicito](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
