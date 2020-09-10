---
title: Imposta il controllo da creare durante il trascinamento
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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7203cc5017763a6ba0b76855f010f114ca879a6
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743100"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati

È possibile creare controlli associati a dati trascinando gli elementi dalla finestra **origini dati** in Progettazione WPF o in Windows Forms Designer. Ogni elemento nella finestra **origini dati** dispone di un controllo predefinito che viene creato quando lo si trascina nella finestra di progettazione. Tuttavia, è possibile scegliere di creare un controllo diverso.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Impostare i controlli da creare per le tabelle o gli oggetti di dati

Prima di trascinare elementi che rappresentano tabelle di dati o oggetti dalla finestra **origini dati** , è possibile scegliere di visualizzare tutti i dati in un controllo o di visualizzare ogni colonna o proprietà in un controllo separato.

In questo contesto, il termine *oggetto* fa riferimento a un oggetto business personalizzato, a un'entità (in un Entity Data Model) o a un oggetto restituito da un servizio.

### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Per impostare i controlli da creare per le tabelle o gli oggetti di dati

1. Assicurarsi che la finestra di progettazione **WPF** o la finestra di progettazione **Windows Forms** sia aperta.

2. Nella finestra **origini dati** selezionare l'elemento che rappresenta la tabella o l'oggetto dati che si desidera impostare.

   > [!TIP]
   > Se la finestra **origini dati** non è aperta, è possibile aprirla selezionando **Visualizza**  >  **altre**  >  **origini dati**di Windows.

3. Fare clic sul menu a discesa per l'elemento, quindi fare clic su uno degli elementi seguenti nel menu:

    - Per visualizzare ogni campo dati in un controllo separato, fare clic su **Dettagli**. Quando si trascina l'elemento dati nella finestra di progettazione, questa azione creerà un controllo con associazione a dati diverso per ogni colonna o proprietà dell'oggetto o della tabella di dati padre, insieme alle etichette per ogni controllo.

    - Per visualizzare tutti i dati in un singolo controllo, selezionare un controllo diverso nell'elenco, ad esempio **DataGrid** o **elenco** in un'applicazione WPF, oppure **DataGridView** in un Windows Forms Application.

    L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET a cui è destinato il progetto e dal fatto che siano stati aggiunti controlli personalizzati che supportano data binding alla **casella degli strumenti**. Se il controllo che si vuole creare non è presente nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

    Per informazioni su come creare un controllo Windows Forms personalizzato che può essere aggiunto all'elenco di controlli per le tabelle di dati o gli oggetti nella finestra **origini dati** , vedere [creare un controllo utente Windows Forms che supporta data binding complesse](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Impostare i controlli da creare per le colonne di dati o le proprietà

Prima di trascinare un elemento che rappresenta una colonna o una proprietà di un oggetto dalla finestra **origini dati** alla finestra di progettazione, è possibile impostare il controllo da creare.

### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Per impostare i controlli da creare per le colonne o le proprietà

1. Assicurarsi che la finestra di progettazione **WPF** o la finestra di progettazione **Windows Forms** sia aperta.

2. Nella finestra **origini dati** espandere la tabella o l'oggetto desiderato per visualizzare le relative colonne o proprietà.

3. Selezionare ogni colonna o proprietà per cui si vuole impostare il controllo da creare.

4. Fare clic sul menu a discesa della colonna o della proprietà, quindi selezionare il controllo che si desidera creare quando l'elemento viene trascinato nella finestra di progettazione.

     L'elenco dei controlli disponibili dipende dalla finestra di progettazione aperta, dalla versione di .NET a cui è destinato il progetto e dai controlli personalizzati che supportano data binding aggiunti alla **casella degli strumenti**. Se il controllo che si vuole creare è nell'elenco dei controlli disponibili, è possibile aggiungere il controllo all'elenco. Per altre informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Per informazioni su come creare un controllo personalizzato che può essere aggiunto all'elenco di controlli per le colonne di dati o le proprietà nella finestra **origini dati** , vedere [creare un Windows Forms controllo utente che supporta data binding semplici](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Se non si desidera creare un controllo per la colonna o la proprietà, selezionare **nessuno** nel menu a discesa. Questa opzione è utile se si desidera trascinare la tabella o l'oggetto padre nella finestra di progettazione, ma non si desidera includere la colonna o la proprietà specifica.

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
