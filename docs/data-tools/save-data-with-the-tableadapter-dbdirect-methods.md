---
title: Salvare dati con i metodi DBDirect di TableAdapter
description: In questa procedura dettagliata eseguire SQL istruzioni direttamente su un database usando i metodi DBDirect di un TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cf7ed024e98382ea134c27cd697cdae932d735d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113783"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare dati con i metodi DBDirect di TableAdapter

Questa procedura dettagliata fornisce istruzioni dettagliate per l'SQL di istruzioni direttamente su un database usando i metodi DBDirect di un TableAdapter. I metodi DBDirect di un oggetto TableAdapter consentono un elevato livello di controllo degli aggiornamenti del database. È possibile usarli per eseguire stored procedure e istruzioni SQL specifiche chiamando i singoli metodi , e in base alle esigenze dell'applicazione (a differenza del metodo di overload che esegue le istruzioni UPDATE, INSERT e DELETE in un'unica `Insert` `Update` `Delete` `Update` chiamata).

Durante questa procedura dettagliata, si apprenderà come:

- Creare una nuova **Windows'applicazione Form.**

- Creare e configurare un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

- Selezionare il controllo da creare nel form tramite il trascinamento degli elementi dalla finestra **Origini dati**. Per altre informazioni, vedere [Impostare il controllo da creare quando si trascina dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creare il controllo associato a dati tramite il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Aggiungere metodi per accedere direttamente al database ed eseguire inserimenti, aggiornamenti ed eliminazioni.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina [di download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express o tramite il Programma di installazione di Visual Studio **.** **Nell'Programma di installazione di Visual Studio** è possibile installare SQL Server Express Local DB come parte  del carico di lavoro Elaborazione ed archiviazione dati o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la finestra **SQL Server Esplora oggetti** dati. (SQL Server Esplora oggetti viene installato come parte del carico **di** lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo. Fare clic con il pulsante destro del mouse sull Local DB e **scegliere Nuova query.**

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query termina e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare **un'Windows'applicazione Form.**

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** **o Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop.**

3. Nel riquadro centrale selezionare il tipo di **progetto Windows app Forms.**

4. Assegnare al **progetto il nome TableAdapterDbDirectMethodsWalkthrough** e quindi scegliere **OK.**

     Il progetto **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database

Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Region` presente nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database di esempio Northwind, [vedere Procedura: Installare database di esempio.](../data-tools/installing-database-systems-tools-and-samples.md)

### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere **Mostra** origini dati dal menu **Dati**.

   Verrà visualizzata la finestra **Origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **Scegliere un tipo di origine** dati selezionare **Database** e quindi selezionare **Avanti.**

4. Nella schermata **Scegliere la connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **Avanti.**

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti.**

7. Nella schermata **Scegliere gli oggetti di** database espandere il **nodo** Tabelle .

8. Selezionare la `Region` tabella e quindi selezionare **Fine.**

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Region` viene visualizzata nella finestra **Origini dati**.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Aggiungere controlli al form per visualizzare i dati

Creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

Per creare controlli associati a dati nel form Windows, trascinare il nodo **Region** principale dalla **finestra** Origini dati nel form.

Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati un oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md) `RegionTableAdapter` , , e <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> .

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter

1. Trascinare tre controlli <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** in **Form1** (sotto l'oggetto **RegionDataGridView**).

2. Impostare le proprietà **Name** e **Text** seguenti per ciascun pulsante.

    |Nome|Testo|
    |----------|----------|
    |`InsertButton`|**Inserimento**|
    |`UpdateButton`|**Aggiornamento**|
    |`DeleteButton`|**Elimina**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database

1. Selezionare **InsertButton per** creare un gestore eventi per l'evento Click e aprire il modulo nell'editor di codice.

2. Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet1":::

### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database

1. Fare doppio clic su **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.

2. Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet2":::

### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere codice per eliminare record dal database

1. Selezionare **DeleteButton per** creare un gestore eventi per l'evento Click e aprire il modulo nell'editor di codice.

2. Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs" id="Snippet3":::

## <a name="run-the-application"></a>Eseguire l'applicazione

- Premere **F5 per** eseguire l'applicazione.

- Selezionare il **pulsante** Inserisci e verificare che il nuovo record venga visualizzato nella griglia.

- Selezionare il **pulsante** Aggiorna e verificare che il record sia aggiornato nella griglia.

- Selezionare il **pulsante** Elimina e verificare che il record venga rimosso dalla griglia.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, è possibile eseguire diversi passaggi dopo la creazione di un form associato a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Aggiunta di funzionalità di ricerca al form.

- Aggiunta di altre tabelle al set di dati tramite selezione di **Configura il Dataset con la procedura guidata** nella finestra **Origini dati**. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form. Per altre informazioni, vedere [Relazioni nei set di dati.](relationships-in-datasets.md)

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
