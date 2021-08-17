---
title: Aggiungere controlli personalizzati alla finestra Origini dati
description: Aggiungere controlli personalizzati alla finestra Origini dati in Visual Studio. Personalizzare l'elenco dei controlli associabili. Aggiungere i controlli associati.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.openlocfilehash: 2b29026eb9242dae0526f6022658f65c4a7b0a76
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067234"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Aggiungere controlli personalizzati alla finestra Origini dati

Quando si trascina un elemento dalla finestra Origini dati in un'area di progettazione per creare un controllo associato a dati, è possibile selezionare il tipo di controllo creato. Ogni elemento nella finestra ha un elenco a discesa che visualizza i controlli tra cui è possibile scegliere. Il set di controlli associato a ogni elemento è determinato dal tipo di dati dell'elemento. Se il controllo che si desidera creare non viene visualizzato nell'elenco, è possibile seguire le istruzioni riportate in questo argomento per aggiungere il controllo all'elenco.

Per altre informazioni sulla selezione di controlli associati a dati da creare per gli elementi nella finestra Origini dati , vedere Impostare il controllo da creare durante il trascinamento dalla [finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Personalizzare l'elenco dei controlli associabili

Per aggiungere o rimuovere controlli dall'elenco dei controlli disponibili per gli elementi della finestra Origini dati con un tipo di dati specifico, seguire questa procedura.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Per selezionare i controlli da visualizzare nell'elenco per un tipo di dati

1. Assicurarsi che WPF Designer o progettazione Windows Form sia aperto.

2. Nella finestra **Origini dati** fare clic su un elemento che fa parte di un'origine dati aggiunta alla finestra e quindi fare clic sul menu a discesa per l'elemento.

   > [!TIP]
   > Se la finestra Origini dati non è aperta, aprirla selezionando Visualizza altre Windows  >    >  **dati**.

3. Nel menu a discesa fare clic su **Personalizza.** Verrà visualizzata una delle finestre di dialogo seguenti:

    - Se **l'Windows Progettazione Form è** aperta, viene visualizzata la pagina Personalizzazione **interfaccia utente** dati della **finestra** di dialogo Opzioni. Per altre informazioni, vedere Finestra [di dialogo Opzioni di personalizzazione dell'interfaccia utente dati](../ide/reference/options-windows-forms-designer-data-ui-customization.md).

    - Se WPF **Designer è aperto,** viene visualizzata **la finestra di dialogo Personalizza** associazione controllo .

4. Nella finestra di dialogo selezionare un tipo di dati **dall'elenco a** discesa Tipo di dati .

    - Per personalizzare l'elenco dei controlli per una tabella o un oggetto, selezionare **[Elenco]**.

    - Per personalizzare l'elenco dei controlli per una colonna di una tabella o una proprietà di un oggetto, selezionare il tipo di dati della colonna o della proprietà nell'archivio dati sottostante.

    - Per personalizzare l'elenco dei controlli per visualizzare gli oggetti dati con forme definite dall'utente, selezionare **[Altro]**. Ad esempio, selezionare **[Altro]** se l'applicazione ha un controllo personalizzato che visualizza i dati di più di una proprietà di un determinato oggetto.

5. Nella **casella Controlli** associati selezionare ogni controllo che si vuole essere disponibile per il tipo di dati selezionato oppure deselezionare i controlli da rimuovere dall'elenco.

    > [!NOTE]
    > Se il controllo che si desidera selezionare non viene visualizzato nella casella **Controlli** associati , è necessario aggiungere il controllo all'elenco. Per altre informazioni, vedere [Aggiungere controlli associati.](#add-associated-controls)

6. Fare clic su **OK**.

7. Nella finestra **Origini dati** fare clic su un elemento del tipo di dati a cui sono stati associati solo uno o più controlli e quindi fare clic sul menu a discesa per l'elemento.

     I controlli selezionati nella casella **Controlli** associati vengono ora visualizzati nel menu a discesa per l'elemento.

## <a name="add-associated-controls"></a>Aggiungere controlli associati

Se si desidera associare un controllo a un tipo di dati, ma il controllo non viene visualizzato nella casella **Controlli** associati , è necessario aggiungere il controllo all'elenco. Il controllo deve trovarsi nella soluzione corrente o in un assembly di riferimento. Deve anche essere disponibile nella casella **degli** strumenti e avere un attributo che specifica il comportamento data binding controllo.

Per aggiungere controlli all'elenco dei controlli associati:

1. Aggiungere il controllo desiderato alla casella degli strumenti **facendo** clic con il pulsante destro del mouse sulla **casella degli** strumenti e scegliendo **Scegli elementi.**

     Il controllo deve avere uno degli attributi seguenti:

    |Attributo|Descrizione|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementare questo attributo in controlli semplici che visualizzano una singola colonna (o proprietà) di dati, ad esempio <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementare questo attributo nei controlli che visualizzano elenchi (o tabelle) di dati, ad esempio <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementare questo attributo nei controlli che visualizzano elenchi (o tabelle) di dati, ma devono anche presentare una singola colonna o proprietà, ad esempio <xref:System.Windows.Forms.ComboBox> .|

2. Per Windows, nella finestra **di dialogo Opzioni** aprire la pagina **Personalizzazione interfaccia utente** dati. In caso contrario, per WPF aprire la **finestra di dialogo Personalizza associazione** controllo . Per altre informazioni, vedere [Personalizzare l'elenco di controlli associabili per un tipo di dati](#customize-the-bindable-controls-list).

3. Nella casella **Controlli associati** dovrebbe essere visualizzato il controllo appena aggiunto **alla** casella degli strumenti.

    > [!NOTE]
    > Solo i controlli che si trovano all'interno della soluzione corrente o in un assembly a cui si fa riferimento possono essere aggiunti all'elenco dei controlli associati. I controlli devono inoltre implementare uno degli attributi di data binding nella tabella precedente. Per associare dati a un controllo personalizzato non disponibile nella finestra  Origini dati , trascinare il controllo dalla  Casella degli strumenti nell'area di progettazione e quindi trascinare l'elemento da associare dalla finestra Origini dati al controllo .

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Finestra di dialogo Opzioni di personalizzazione dell'interfaccia utente dati](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
