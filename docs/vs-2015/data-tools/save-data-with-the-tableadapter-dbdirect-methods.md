---
title: Salvare i dati con i metodi DBDirect di TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655415"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare dati con i metodi DBDirect di TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata vengono fornite istruzioni dettagliate per l'esecuzione di istruzioni SQL direttamente in un database utilizzando i metodi DBDirect di un TableAdapter. I metodi DBDirect di un oggetto TableAdapter consentono un elevato livello di controllo degli aggiornamenti del database. È possibile utilizzarli per eseguire istruzioni SQL e stored procedure specifiche chiamando i singoli metodi `Insert`, `Update` e `Delete` in base alle esigenze dell'applicazione (anziché il metodo di `Update` di overload che esegue l'aggiornamento, inserire e le istruzioni DELETE in una sola chiamata).

 Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova **applicazione Windows**.

- Creare e configurare un set di dati con la [Configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Selezionare il controllo da creare nel form tramite il trascinamento degli elementi dalla finestra **Origini dati**. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creare il controllo associato a dati tramite il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Aggiungere metodi per accedere direttamente al database ed eseguire inserimenti, aggiornamenti ed eliminazioni.

## <a name="prerequisites"></a>Prerequisites
 Per completare questa procedura dettagliata, è necessario:

- Accedere al database di esempio Northwind.

## <a name="create-a-windows-application"></a>Creare un'applicazione Windows
 Il primo passaggio consiste nel creare un' **applicazione Windows**.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, nel menu **file** , creare un nuovo **progetto**.

2. Denominare il progetto **TableAdapterDbDirectMethodsWalkthrough**.

3. Selezionare **applicazione Windows**e quindi fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database
 Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Region` presente nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Mostra origini dati**dal menu **dati** .

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati** selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         oppure

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database** espandere il nodo **tabelle** .

8. Selezionare la tabella `Region`, quindi fare clic su **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Region` viene visualizzata nella finestra **Origini dati**.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols al form per visualizzare i dati
 Creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare controlli associati a dati in Windows Form

- Trascinare il nodo **area** principale dalla finestra **origini dati** nel form.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati un oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter

1. Trascinare tre controlli <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** in **Form1** (sotto l'oggetto **RegionDataGridView**).

2. Impostare le proprietà **Name** e **Text** seguenti per ciascun pulsante.

    |Name|Testo|
    |----------|----------|
    |`InsertButton`|**Inserisci**|
    |`UpdateButton`|**Aggiornamento**|
    |`DeleteButton`|**Eliminazione**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database

1. Selezionare **InsertButton** per creare un gestore eventi per l'evento click e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database

1. Fare doppio clic su **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere il codice per eliminare i record dal database

1. Selezionare **DeleteButton** per creare un gestore eventi per l'evento click e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

- Selezionare **F5** per eseguire l'applicazione.

- Selezionare il pulsante **Inserisci** e verificare che il nuovo record venga visualizzato nella griglia.

- Selezionare il pulsante **Aggiorna** e verificare che il record sia stato aggiornato nella griglia.

- Selezionare il pulsante **Elimina** e verificare che il record sia stato rimosso dalla griglia.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diversi passaggi dopo la creazione di un form associato a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Aggiunta di funzionalità di ricerca al form. Per altre informazioni, vedere [procedura: aggiungere una query con parametri a un'applicazione Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Aggiunta di altre tabelle al set di dati tramite selezione di **Configura il Dataset con la procedura guidata** nella finestra **Origini dati**. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form.

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
