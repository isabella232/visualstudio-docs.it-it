---
title: Implementare un'interfaccia
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 58c714dec8b8a4679d34168cdaf901dc2fb94ea6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974790"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementare un'interfaccia in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice necessario per implementare un'interfaccia.

**Quando:** si vuole ereditare da un'interfaccia.

**Perché?:** è possibile implementare manualmente tutte le interfacce, una alla volta. Questa funzionalità, tuttavia, genera automaticamente tutte le firme dei metodi.

## <a name="how-to"></a>Procedura

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato aggiunto un riferimento a un'interfaccia, ma che non sono stati implementati tutti i membri obbligatori.

   - C#:

       ![Codice evidenziato C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Codice evidenziato VB](media/interface-highlight-vb.png)

2. Eseguire quindi una delle operazioni seguenti:

   - **Tastiera**
      - Premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina di errore](media/error-bulb.png) visualizzata.
      - Fare clic sul pulsante ![lampadina di errore](media/error-bulb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

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

## <a name="see-also"></a>Vedere anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)