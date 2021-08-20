---
title: Opzioni, Progettazione Windows Form, Personalizzazione dell'interfaccia utente dati
description: Informazioni su come usare la pagina Personalizzazione dell'interfaccia utente dati per definire i controlli da visualizzare nell'elenco dei controlli disponibili per gli elementi nella finestra Origini dati.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 6e419f144b44076e1108988cf1123a6a87b410ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151184"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Finestra di dialogo Opzioni: Finestra Windows Form > personalizzazione dell'interfaccia utente dati

Questa finestra di dialogo consente di definire i controlli che vengono visualizzati nell'elenco dei controlli disponibili per gli elementi nella finestra Origini dati. Per aprirlo, selezionare **Opzioni** strumenti e quindi selezionare Windows personalizzazione dell'interfaccia utente dati  >  di   >  **Progettazione Form.**

È possibile selezionare un controllo da un elemento nella finestra Origini dati prima di trascinarlo nel form in un'app Windows Form. I controlli disponibili sono determinati dal tipo di dati dell'elemento. Ogni tipo di dati ha un elenco di controlli associati validi, come definito in questa finestra di dialogo, incluso un controllo predefinito. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

Personalizzare l'elenco dei controlli associati selezionando e deselezionando le caselle di controllo dei controlli disponibili per ogni tipo di dati. Per aggiungere un controllo all'elenco, aggiungere un controllo che implementi l'attributo di associazione dati <xref:System.ComponentModel.DefaultBindingPropertyAttribute> o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> alla casella degli strumenti. Il controllo verrà quindi visualizzato nell'elenco dei controlli per il tipo di dati. Per altre informazioni, [vedere Procedura: Aggiungere controlli personalizzati alla finestra Origini dati](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo di dati

Visualizza un elenco di tipi a cui si associano i controlli. Le tabelle vengono rappresentate come il tipo di dati `[List]`. Le colonne vengono rappresentate come il tipo di dati effettivo della colonna nell'archivio dati sottostante.

## <a name="associated-controls"></a>Controlli associati

Visualizza un elenco di controlli associati al tipo di dati selezionato. Selezionare o deselezionare la casella di controllo accanto al controllo per associarlo o rimuoverne l'associazione. I controlli selezionati vengono visualizzati nella finestra Origini dati per una colonna di database associata al tipo di dati associato.

## <a name="set-default"></a>Imposta predefinito

Assegna il tipo di controllo selezionato come predefinito per il tipo di dati selezionato. Il controllo predefinito viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database nella finestra Origini dati. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

È possibile assegnare un solo tipo di controllo come predefinito per un tipo di dati.

## <a name="clear-default"></a>Cancella predefinito

Rimuove la designazione di un controllo come predefinito per il tipo di dati selezionato. Se non è disponibile alcun valore predefinito per il tipo di dati selezionato, `[None]` viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database di tale tipo.
