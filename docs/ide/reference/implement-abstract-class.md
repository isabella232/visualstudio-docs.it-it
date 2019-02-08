---
title: Implementare una classe astratta
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c9927f810dabd028cba311a576e2bbc33a398f5
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483952"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementare una classe astratta in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice necessario per implementare una classe astratta.

**Quando:** si vuole ereditare da una classe astratta.

**Perché?:** è possibile implementare manualmente tutti i membri astratti, uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica l'ereditarietà da una classe astratta, ma che non sono stati implementati tutti i membri obbligatori.

   - C#:

       ![Codice evidenziato C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/abstract-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina di errore](media/error-bulb.png) visualizzata.
      - Fare clic sul pulsante ![lampadina di errore](media/error-bulb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima dell'implementazione della classe](media/abstract-preview-cs.png)

3. Scegliere **Implementa classe astratta** dal menu a discesa.

   > [!TIP]
   > - Usare il collegamento **Anteprima modifiche** nella parte inferiore della finestra di anteprima [per visualizzare tutte le modifiche](../../ide/preview-changes.md) che verranno apportate prima di effettuare la selezione.
   > - Usare i collegamenti **Documento**, **Progetto** e **Soluzione** nella parte inferiore della finestra di anteprima per creare le firme dei metodi appropriate per più classi che ereditano dalla classe astratta.

   Le firme dei metodi astratti vengono create e sono pronte per l'implementazione.

   - C#:

       ![Risultato dell'implementazione della classe C#](media/abstract-result-cs.png)

   - Visual Basic:

       ![Risultato dell'implementazione della classe VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)