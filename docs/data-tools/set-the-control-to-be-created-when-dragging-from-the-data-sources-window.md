---
title: Impostare il controllo da creare durante il trascinamento
description: Informazioni su come impostare il controllo da creare quando si trascina dalla finestra Origini dati alla finestra di progettazione WPF o Windows Form in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1033ffad781efe15507c5a484cd83f88a837d00fb6bc28fc5df78404076d6361
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346830"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati

È possibile creare controlli associati a  dati trascinando gli elementi dalla finestra Origini dati alla finestra di progettazione WPF Windows Progettazione form. Ogni elemento nella **finestra Origini dati** ha un controllo predefinito che viene creato quando lo si trascina nella finestra di progettazione. È tuttavia possibile scegliere di creare un controllo diverso.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Impostare i controlli da creare per tabelle o oggetti dati

Prima di trascinare gli elementi che  rappresentano tabelle o oggetti di dati dalla finestra Origini dati, è possibile scegliere di visualizzare tutti i dati in un unico controllo o di visualizzare ogni colonna o proprietà in un controllo separato.

In questo contesto, il *termine* oggetto fa riferimento a un oggetto business personalizzato, a un'entità (in un Entity Data Model) o a un oggetto restituito da un servizio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Per impostare i controlli da creare per tabelle o oggetti dati

1. Assicurarsi che la finestra **di progettazione WPF** o Windows **Form** sia aperta.

2. Nella finestra **Origini dati** selezionare l'elemento che rappresenta la tabella o l'oggetto dati da impostare.

   > [!TIP]
   > Se la **finestra Origini** dati non è aperta, è possibile aprirla selezionando Visualizza Windows   >    >  **origini dati**.

3. Fare clic sul menu a discesa per l'elemento e quindi su una delle voci seguenti nel menu:

    - Per visualizzare ogni campo dati in un controllo separato, fare clic su **Dettagli**. Quando si trascina l'elemento di dati nella finestra di progettazione, questa azione crea un controllo associato a dati diverso per ogni colonna o proprietà della tabella o dell'oggetto dati padre, insieme alle etichette per ogni controllo.

    - Per visualizzare tutti i dati in un singolo controllo, selezionare un controllo diverso nell'elenco, ad esempio **DataGrid** o **List** in un'applicazione WPF o **DataGridView** in un'applicazione Windows Forms.

    L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET di destinazione del progetto e dal fatto che siano stati aggiunti controlli personalizzati che supportano data binding alla casella **degli strumenti**. Se il controllo da creare non è presente nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Per informazioni su come creare un controllo Windows Forms personalizzato che può essere aggiunto  all'elenco di controlli per tabelle o oggetti dati nella finestra Origini dati, vedere Creare un controllo utente [Windows Forms](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)che supporta oggetti data binding .

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Impostare i controlli da creare per le colonne di dati o le proprietà

Prima di trascinare un elemento che rappresenta una  colonna o una proprietà di un oggetto dalla finestra Origini dati alla finestra di progettazione, è possibile impostare il controllo da creare.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Per impostare i controlli da creare per colonne o proprietà

1. Assicurarsi che la finestra **di progettazione WPF** o Windows **Form** sia aperta.

2. Nella finestra **Origini dati** espandere la tabella o l'oggetto desiderato per visualizzarne le colonne o le proprietà.

3. Selezionare ogni colonna o proprietà per cui si vuole impostare il controllo da creare.

4. Fare clic sul menu a discesa per la colonna o la proprietà e quindi selezionare il controllo da creare quando l'elemento viene trascinato nella finestra di progettazione.

     L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET di destinazione del progetto e dai controlli personalizzati che supportano data binding aggiunti alla casella **degli strumenti**. Se il controllo da creare si trova nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Per informazioni su come creare un controllo personalizzato che può essere aggiunto  all'elenco di controlli per le colonne di dati o le proprietà nella finestra Origini dati, vedere Creare un controllo utente [Windows Forms](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)che supporti l'data binding .

     Se non si vuole creare un controllo per la colonna o la proprietà, selezionare **Nessuno** nel menu a discesa. Ciò è utile se si vuole trascinare la tabella o l'oggetto padre nella finestra di progettazione, ma non si vuole includere la colonna o la proprietà specifica.

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
