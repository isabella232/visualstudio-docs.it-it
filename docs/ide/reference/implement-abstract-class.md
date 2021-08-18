---
title: Implementare una classe astratta
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare immediatamente il codice necessario per implementare una classe astratta.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 201ebe54d84803ab0621afd5754ce507b1d32ac7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101310"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementare una classe astratta in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice necessario per implementare una classe astratta.

**Quando:** si vuole ereditare da una classe astratta.

**Perché:** è possibile implementare manualmente tutti i membri astratti, uno alla volta, tuttavia questa funzionalità genera automaticamente tutte le firme dei metodi.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica l'ereditarietà da una classe astratta, ma che non sono stati implementati tutti i membri obbligatori.

   - C#:

       ![Codice evidenziato C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/abstract-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina di errore](media/error-bulb.png) visualizzata.
      - Fare clic sull'icona ![lampadina di errore](media/error-bulb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

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

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
