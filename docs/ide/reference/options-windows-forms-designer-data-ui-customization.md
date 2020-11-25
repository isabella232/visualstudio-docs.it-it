---
title: Opzioni, Progettazione Windows Form, Personalizzazione dell'interfaccia utente dati
description: Informazioni su come utilizzare la pagina di personalizzazione dell'interfaccia utente dati per definire quali controlli vengono visualizzati nell'elenco dei controlli disponibili per gli elementi nella finestra Origini dati.
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
manager: jillfra
ms.openlocfilehash: 2b43776d2218f6f2a6a120e139dcae9d540f6f10
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040095"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Finestra di dialogo Opzioni: Progettazione Windows Form > personalizzazione dell'interfaccia utente dei dati

Questa finestra di dialogo consente di definire i controlli che vengono visualizzati nell'elenco dei controlli disponibili per gli elementi nella finestra Origini dati. Per aprirlo, selezionare **strumenti**  >  **Opzioni** e quindi selezionare **Progettazione Windows Form**  >  **personalizzazione dell'interfaccia utente dati**.

È possibile selezionare un controllo da un elemento nella finestra Origini dati prima di trascinarlo nel form in un'app Windows Form. I controlli disponibili sono determinati dal tipo di dati dell'elemento. Ogni tipo di dati ha un elenco di controlli associati validi, come definito in questa finestra di dialogo, incluso un controllo predefinito. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

Personalizzare l'elenco dei controlli associati selezionando e deselezionando le caselle di controllo dei controlli disponibili per ogni tipo di dati. Per aggiungere un controllo all'elenco, aggiungere un controllo che implementi l'attributo di associazione dati <xref:System.ComponentModel.DefaultBindingPropertyAttribute> o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> alla casella degli strumenti. Il controllo verrà quindi visualizzato nell'elenco dei controlli per il tipo di dati. Per altre informazioni, vedere [procedura: aggiungere controlli personalizzati alla finestra Origini dati](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo di dati

Visualizza un elenco di tipi a cui si associano i controlli. Le tabelle vengono rappresentate come il tipo di dati `[List]`. Le colonne vengono rappresentate come il tipo di dati effettivo della colonna nell'archivio dati sottostante.

## <a name="associated-controls"></a>Controlli associati

Visualizza un elenco di controlli associati al tipo di dati selezionato. Selezionare o deselezionare la casella di controllo accanto al controllo per associarlo o rimuoverne l'associazione. I controlli selezionati vengono visualizzati nella finestra Origini dati per una colonna di database associata al tipo di dati associato.

## <a name="set-default"></a>Imposta predefinito

Assegna il tipo di controllo selezionato come predefinito per il tipo di dati selezionato. Il controllo predefinito viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database nella finestra Origini dati. Quando si trascina un elemento dalla finestra Origini dati in un form senza selezionare un controllo, il controllo predefinito per il tipo di dati dell'elemento selezionato viene aggiunto al form.

È possibile assegnare un solo tipo di controllo come predefinito per un tipo di dati.

## <a name="clear-default"></a>Cancella predefinito

Rimuove la designazione di un controllo come predefinito per il tipo di dati selezionato. Se non è disponibile alcun valore predefinito per il tipo di dati selezionato, `[None]` viene visualizzato come prima selezione nel menu di scelta rapida per una colonna di database di tale tipo.
