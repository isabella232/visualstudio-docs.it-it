---
title: Generare un costruttore - Generazione del codice (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>Generare un costruttore in C# #
**Cosa:** consente di generare immediatamente il codice per un nuovo costruttore in una classe. 

**Quando:** si introduce un nuovo costruttore e si vuole dichiararlo in modo corretto, automaticamente, oppure si vuole modificare un costruttore esistente. 

**Perché:** si potrebbe dichiarare il costruttore prima di usarlo, tuttavia questa funzionalità consente di generarlo automaticamente, con i parametri appropriati. Inoltre, la modifica di un costruttore esistente richiede l'aggiornamento di tutti i siti di chiamata, a meno che non si usi questa funzionalità per aggiornarli automaticamente.

**Procedura:** esistono diversi modi per generare un costruttore:
- [Generare un costruttore e selezionare i membri](#pick)
- [Generare un costruttore dai campi selezionati](#selection)
- [Generare un costruttore da un nuovo utilizzo](#usage)
- [Aggiungere un parametro a un costruttore esistente](#addparameter)
- [Creare e inizializzare un campo/una proprietà dal parametro di un costruttore](#create)

## <a id = "pick"></a> Generare un costruttore e selezionare i membri
1. Posizionare il cursore in qualsiasi riga vuota in una classe:

   ![Cursore in una riga vuota](media/constructor1-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera costruttore** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera costruttore** dal popup della finestra di anteprima.
     * Fare clic sull'icona ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga vuota nella classe.

   ![Anteprima della generazione di un costruttore](media/constructor1-preview-cs.png)

1. Verrà visualizzata una finestra di dialogo che consente di scegliere i membri che si vuole usare come parametri del costruttore nonché di ordinarli (con le frecce su e giù). Fare clic su **OK** per eseguire il commit delle modifiche.
  
   ![Finestra di dialogo Seleziona membri](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >È possibile selezionare la casella di controllo **Aggiungi i controlli Null** per generare automaticamente i controlli Null per i parametri del costruttore.

1. Il costruttore verrà creato con i parametri selezionati nell'ordine specificato.
   ![Risultato della generazione del costruttore](media/constructor1-result-cs.png)

## <a id="selection"></a> Generare un costruttore dai campi selezionati
1. Evidenziare i membri che si desidera includere nel costruttore generato: ![Evidenziare i membri](media/constructor2-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera il costruttore 'NomeTipo (...)'** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera il costruttore 'NomeTipo (...)'** dal popup della finestra di anteprima.
     * Fare clic sull'icona ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la selezione.

     ![Anteprima della generazione di un costruttore](media/constructor2-preview-cs.png)

1. Il costruttore verrà creato con i parametri selezionati.
     ![Risultato della generazione del costruttore](media/constructor2-result-cs.png)

## <a id="usage"></a> Generare un costruttore da un nuovo utilizzo
1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato usato un costruttore che non esiste ancora.

   ![Codice evidenziato](media/constructor-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Genera il costruttore in '*NomeTipo*'** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Genera il costruttore in '*NomeTipo*'** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Anteprima della generazione di un costruttore](media/constructor-preview-cs.png)

   >[!TIP]
   >Usare il collegamento [**Anteprima modifiche**](../../ide/preview-changes.md) nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche che verranno apportate prima di effettuare la selezione.

1. Il costruttore verrà creato automaticamente con gli eventuali parametri dedotti dal relativo utilizzo.

   ![Risultato della generazione del costruttore](media/constructor-result-cs.png)

## <a id="addparameter"></a> Aggiungere un parametro a un costruttore esistente
1. Aggiungere un parametro a un'istanza di oggetto esistente.

1. Posizionare il cursore nella riga in cui è presente una sottolineatura ondulata rossa che indica che è stato usato un costruttore che non esiste ancora.
    
    ![Evidenziazione per generare un costruttore](media/constructor4-highlight-cs.png)

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Aggiungi il parametro a 'NomeTipo (...)'** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Aggiungi il parametro a 'NomeTipo (...)'** dal popup della finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa ondulata e fare clic sull'icona a forma di ![lampadina](media/bulb-cs.png) visualizzata.
     * Fare clic sul pulsante ![lampadina](media/bulb-cs.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con la sottolineatura ondulata rossa.

    ![Anteprima della generazione di un costruttore](media/constructor4-preview-cs.png)

1. Il parametro verrà aggiunto automaticamente con il tipo dedotto dal relativo utilizzo.
   
   ![Risultato della generazione del costruttore](media/constructor4-result-cs.png)

## <a id="create"></a> Creare e inizializzare un campo/una proprietà dal parametro di un costruttore
1. Da un costruttore esistente, aggiungere un parametro:

   ![Evidenziazione per generare un costruttore](media/constructor5-highlight-cs.png)

1. Posizionare il cursore all'interno del parametro appena aggiunto.

1. Eseguire quindi una delle operazioni seguenti:
   * **Tastiera**
     * Premere **CTRL+.** per attivare il menu **Azioni rapide e refactoring** e selezionare **Crea e inizializza la proprietà 'Proprietà'** o **Crea e inizializza il campo 'Campo'** dal popup della finestra di anteprima.
   * **Mouse**
     * Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**, quindi selezionare **Crea e inizializza la proprietà 'Proprietà'** o **Crea e inizializza il campo 'Campo'** dal popup della finestra di anteprima.
     * Fare clic sull'icona ![lampadina](media/bulb-cs.png) visualizzata nel margine sinistro se il cursore del testo si trova già nella riga con il parametro aggiunto.

   ![Anteprima della generazione di un costruttore](media/constructor5-preview-cs.png)

1. Il campo o la proprietà verrà creato automaticamente con un nome corrispondente ai tipi.

   ![Risultato della generazione del costruttore](media/constructor5-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)