---
title: Opzioni, Progettazione Windows Form, Personalizzazione dell'interfaccia utente dati
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ca68a944002d743c6f3d2f89b309b8b77c5dfdb3
ms.sourcegitcommit: 6b0503ed8d25454d6e39a8e606910b3fa58cf1d2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68981687"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Finestra di dialogo Opzioni: Progettazione Windows Form > Personalizzazione dell'interfaccia utente dati

Questa finestra di dialogo consente di definire i controlli che vengono visualizzati nell'elenco dei controlli disponibili per gli elementi nella finestra Origini dati. Per aprirla, selezionare **Strumenti** > **Opzioni** e quindi selezionare **Progettazione Windows Form** >  **Personalizzazione dell'interfaccia utente dati**.

È possibile selezionare un controllo da un elemento nella finestra Origini dati prima di trascinarlo nel form in un'app Windows Form. I controlli disponibili sono determinati dal tipo di dati dell'elemento. Ogni tipo di dati ha un elenco di controlli associati validi, come definito in questa finestra di dialogo, incluso un controllo predefinito. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

Personalizzare l'elenco dei controlli associati selezionando e deselezionando le caselle di controllo dei controlli disponibili per ogni tipo di dati. Per aggiungere un controllo all'elenco, aggiungere un controllo che implementi l'attributo di associazione dati <xref:System.ComponentModel.DefaultBindingPropertyAttribute> o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> alla casella degli strumenti. Il controllo verrà quindi visualizzato nell'elenco dei controlli per il tipo di dati. Per altre informazioni, vedere [Procedura: Aggiungere controlli personalizzati alla finestra Origini dati](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo di dati

Visualizza un elenco di tipi a cui si associano i controlli. Le tabelle vengono rappresentate come il tipo di dati `[List]`. Le colonne vengono rappresentate come il tipo di dati effettivo della colonna nell'archivio dati sottostante.

## <a name="associated-controls"></a>Controlli associati

Visualizza un elenco di controlli associati al tipo di dati selezionato. Selezionare o deselezionare la casella di controllo accanto al controllo per associarlo o rimuoverne l'associazione. I controlli selezionati vengono visualizzati nella finestra Origini dati per una colonna di database associata al tipo di dati associato.

## <a name="set-default"></a>Imposta predefinito

Assegna il tipo di controllo selezionato come predefinito per il tipo di dati selezionato. Il controllo predefinito viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database nella finestra Origini dati. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

È possibile assegnare un solo tipo di controllo come predefinito per un tipo di dati.

## <a name="clear-default"></a>Cancella predefinito

Rimuove la designazione di un controllo come predefinito per il tipo di dati selezionato. Se non è disponibile alcun valore predefinito per il tipo di dati selezionato, `[None]` viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database di tale tipo.