---
title: Generare una classe o un tipo - Generazione del codice (Visual Basic) | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 4a4ff45a59fb53964a365f31cc4d5f48a5b159dc
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Generare una classe o un tipo in Visual Basic
**Cosa:** consente di generare immediatamente il codice per una classe o un tipo. 

**Quando:** si introduce una nuova classe o un nuovo tipo e si vuole dichiararlo in modo corretto, automaticamente.  

**Perché:** si potrebbe dichiarare la classe o il tipo prima dell'uso, tuttavia questa funzionalità genera la classe o il tipo automaticamente. 

**Come:**

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stata usata una classe che non esiste ancora.

   ![Codice evidenziato](media/class-highlight-vb.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare una delle opzioni dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare una delle opzioni dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-vb.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-vb.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima della generazione della classe](media/class-preview-vb.png)

   Selection | Descrizione
   --- | ---
   Generare l'elemento classe '*NomeTipo*' nel nuovo file | Crea una classe denominata *NomeTipo* in un file denominato *NomeTipo*.cs/.vb
   Genera classe '*NomeTipo*' | Crea una classe denominata *NomeTipo* nel file corrente.
   Genera l'elemento classe '*NomeTipo*' annidato | Crea una classe denominata *NomeTipo* annidata nella classe corrente.
   Genera nuovo tipo | Crea una nuova classe o un nuovo struct con tutte le proprietà specificate.

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. Se si seleziona **Genera nuovo tipo** verrà visualizzata una finestra di dialogo che consente di eseguire alcune azioni aggiuntive.

   ![Genera tipo](media/class-newtype-vb.png)

   Selection | Descrizione
   --- | ---
   Accedi a | Impostare il tipo per l'accesso *Predefinito*, *Interno* o *Pubblico*.
   Kind | Può essere impostato come *classe* o *struct*.
   nome | Questo non può essere modificato e sarà il nome già digitato.
   Progetto | Se sono presenti più progetti nella soluzione, è possibile scegliere il progetto in cui aggiungere la classe/lo struct.
   Nome file | È possibile creare un nuovo file oppure è possibile aggiungere il tipo a un file esistente.

1. La classe o lo struct verrà creato automaticamente con il costruttore dedotto dal relativo utilizzo.

   ![Risultato della generazione della classe](media/class-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)