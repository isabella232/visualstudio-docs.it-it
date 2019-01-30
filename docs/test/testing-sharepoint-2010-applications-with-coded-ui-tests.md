---
title: Testare applicazioni SharePoint con test codificati dell'interfaccia utente
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a4b79531948310d0f2628b6ade334d6ea9df35ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946014"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testare applicazioni SharePoint con test codificati dell'interfaccia utente

Includendo i test codificati dell'interfaccia utente in un'applicazione SharePoint è possibile verificare che l'intera applicazione, inclusi i controlli per l'interfaccia utente, siano correttamente funzionanti. I test codificati dell'interfaccia utente possono inoltre convalidare i valori e la logica dell'interfaccia utente.

Per altre informazioni sui vantaggi derivanti dall'uso di test codificati dell'interfaccia utente, vedere [Usare l'automazione dell'interfaccia utente per testare il codice](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisiti**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Creare un test codificato dell'interfaccia utente per un'app SharePoint

La [creazione di test codificati dell'interfaccia utente](../test/use-ui-automation-to-test-your-code.md) per le applicazioni SharePoint è analoga alla creazione dei test per altri tipi di applicazioni. La registrazione e la riproduzione sono supportate da tutti i controlli dell'interfaccia di **modifica Web**. L'interfaccia per selezionare le categorie e le Web part è costituita da soli controlli Web standard.

![Web part di SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Se si sta registrando l'azione, convalidare le azioni prima di generare il codice. Poiché esistono numerosi comportamenti associati al passaggio del mouse, l'opzione è attivata per impostazione predefinita. Assicurarsi di rimuovere i passaggi del mouse ridondanti dai test codificati dell'interfaccia utente. È possibile eseguire questa operazione modificando il codice del test o tramite l' [editor di test codificati dell'interfaccia utente](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Testare i controlli di Office in un'app SharePoint

Per abilitare l'automazione di alcune Web part di Office in un'app SharePoint, è necessario apportare alcune piccole modiche al codice.

> [!NOTE]
> Il test dei controlli Visio e PowerPoint nelle app di SharePoint non è supportato.

### <a name="excel-cell-controls"></a>Controlli della cella di Excel

Per includere i controlli della cella di Excel, è necessario apportare alcune modifiche nel codice del test codificato dell'interfaccia utente.

> [!WARNING]
> L'inserimento del testo in una cella di Excel seguito da un'azione con tasto di direzione, non viene registrato correttamente. Utilizzare il mouse per selezionare le celle.

Se si eseguono azioni di registrazione su una cella vuota, è necessario modificare il codice facendo doppio clic sulla cella e quindi eseguendo un'operazione di impostazione del testo. Ciò è necessario perché un clic nella cella, seguito da qualsiasi azione della tastiera attiva l'elemento `textarea` all'interno della cella. Registrando un elemento `setvalue` sulla cella vuota viene eseguita la ricerca dell'elemento `editbox` che non è presente fino a quando la cella non viene selezionata. Ad esempio:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Se si eseguono azioni di registrazione su una cella non vuota, la registrazione diviene leggermente più complessa perché quando si aggiunge il testo in una cella, viene aggiunto un nuovo controllo \<div> come elemento figlio della cella. Il nuovo controllo \<div> contiene il testo appena immesso. Il registratore deve registrare le azioni nel nuovo controllo \<div>, ma non può perché il controllo \<div> non esiste finché il test non viene immesso. È necessario apportare manualmente le seguenti modifiche al codice per ovviare a questo problema.

1. Passare all'inizializzazione della cella e rendere primarie le proprietà `RowIndex` e `ColumnIndex` :

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Individuare l'elemento figlio `HtmlDiv` della cella:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Aggiungere il codice per un'azione doppio clic del mouse su `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Aggiungere il codice per impostare il testo su `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
