---
title: Aggiungere controlli personalizzati alla finestra Origini dati
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
manager: jillfra
ms.openlocfilehash: 39ff272581793be9b456bbc404119a488850b3c4
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283073"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Aggiungere controlli personalizzati alla finestra Origini dati

Quando si trascina un elemento dalla finestra Origini dati a un'area di progettazione per creare un controllo con associazione a dati, è possibile selezionare il tipo di controllo creato. Ogni elemento della finestra dispone di un elenco a discesa in cui sono visualizzati i controlli tra cui è possibile scegliere. Il set di controlli associato a ogni elemento è determinato dal tipo di dati dell'elemento. Se il controllo che si desidera creare non viene visualizzato nell'elenco, è possibile seguire le istruzioni riportate in questo argomento per aggiungere il controllo all'elenco.

Per ulteriori informazioni sulla selezione di controlli associati a dati da creare per gli elementi nella finestra Origini dati, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="customize-the-bindable-controls-list"></a>Personalizzare l'elenco di controlli associabili

Per aggiungere o rimuovere controlli dall'elenco dei controlli disponibili per gli elementi nella finestra Origini dati con un tipo di dati specifico, seguire questa procedura.

### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Per selezionare i controlli da elencare per un tipo di dati

1. Verificare che la finestra di progettazione WPF o la Progettazione Windows Form sia aperta.

2. Nella finestra **origini dati** fare clic su un elemento che fa parte di un'origine dati aggiunta alla finestra, quindi fare clic sul menu a discesa per l'elemento.

   > [!TIP]
   > Se la finestra Origini dati non è aperta, aprirla selezionando **Visualizza**  >  **altre**  >  **origini dati**di Windows.

3. Nel menu a discesa fare clic su **Personalizza**. Si apre una delle finestre di dialogo seguenti:

    - Se la **Progettazione Windows Form** è aperta, viene visualizzata la pagina **personalizzazione interfaccia utente dati** della finestra di dialogo **Opzioni** . Per altre informazioni, vedere [finestra di dialogo Opzioni di personalizzazione dell'interfaccia utente dati](../ide/reference/options-windows-forms-designer-data-ui-customization.md).

    - Se **WPF Designer** è aperto, viene visualizzata la finestra di dialogo **Personalizza associazione di controlli** .

4. Nella finestra di dialogo selezionare un tipo di dati nell'elenco a discesa **tipo di dati** .

    - Per personalizzare l'elenco di controlli per una tabella o un oggetto, selezionare **[list]**.

    - Per personalizzare l'elenco di controlli per una colonna di una tabella o una proprietà di un oggetto, selezionare il tipo di dati della colonna o della proprietà nell'archivio dati sottostante.

    - Per personalizzare l'elenco di controlli per la visualizzazione di oggetti dati con forme definite dall'utente, selezionare **[altro]**. Ad esempio, selezionare **[altro]** se l'applicazione dispone di un controllo personalizzato che Visualizza i dati da più di una proprietà di un oggetto specifico.

5. Nella casella **controlli associati** selezionare ogni controllo che si desidera sia disponibile per il tipo di dati selezionato oppure deselezionare la selezione di tutti i controlli che si desidera rimuovere dall'elenco.

    > [!NOTE]
    > Se il controllo che si desidera selezionare non viene visualizzato nella casella **controlli associati** , è necessario aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiungere controlli associati](#add-associated-controls).

6. Fare clic su **OK**.

7. Nella finestra **origini dati** fare clic su un elemento del tipo di dati a cui è stato appena associato uno o più controlli, quindi fare clic sul menu a discesa per l'elemento.

     I controlli selezionati nella casella **controlli associati** sono ora visualizzati nel menu a discesa per l'elemento.

## <a name="add-associated-controls"></a>Aggiungere controlli associati

Se si desidera associare un controllo a un tipo di dati, ma il controllo non viene visualizzato nella casella **controlli associati** , è necessario aggiungere il controllo all'elenco. Il controllo deve trovarsi nella soluzione corrente o in un assembly a cui si fa riferimento. Deve inoltre essere disponibile nella **casella degli strumenti** e avere un attributo che specifichi il comportamento del data binding del controllo.

Per aggiungere controlli all'elenco di controlli associati:

1. Aggiungere il controllo desiderato alla **casella degli strumenti** facendo clic con il pulsante destro del mouse sulla **casella degli strumenti** e scegliendo **Scegli elementi**.

     Il controllo deve avere uno degli attributi seguenti:

    |Attributo|Descrizione|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implementare questo attributo nei controlli semplici che visualizzano una singola colonna (o proprietà) di dati, ad esempio un oggetto <xref:System.Windows.Forms.TextBox> .|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implementare questo attributo sui controlli che visualizzano elenchi o tabelle di dati, ad esempio un oggetto <xref:System.Windows.Forms.DataGridView> .|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implementare questo attributo sui controlli che visualizzano elenchi (o tabelle) di dati, ma che devono anche presentare una singola colonna o proprietà, ad esempio <xref:System.Windows.Forms.ComboBox> .|

2. Per Windows Forms, nella finestra di dialogo **Opzioni** aprire la pagina **personalizzazione interfaccia utente dati** . In alternativa, per WPF aprire la finestra di dialogo **Personalizza binding del controllo** . Per ulteriori informazioni, vedere [personalizzare l'elenco di controlli associabili per un tipo di dati](#customize-the-bindable-controls-list).

3. Nella casella **controlli associati** verrà visualizzato il controllo appena aggiunto alla **casella degli strumenti** .

    > [!NOTE]
    > Solo i controlli che si trovano all'interno della soluzione corrente o in un assembly a cui si fa riferimento possono essere aggiunti all'elenco di controlli associati. I controlli devono inoltre implementare uno degli attributi di data binding nella tabella precedente. Per associare dati a un controllo personalizzato che non è disponibile nella finestra Origini dati, trascinare il controllo dalla **casella degli strumenti** nell'area di progettazione, quindi trascinare l'elemento da associare a dalla finestra **origini dati** nel controllo.

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Finestra di dialogo Opzioni di personalizzazione dell'interfaccia utente dati](../ide/reference/options-windows-forms-designer-data-ui-customization.md)
