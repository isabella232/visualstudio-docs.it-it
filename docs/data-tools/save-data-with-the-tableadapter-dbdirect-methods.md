---
title: Salvare dati con i metodi DBDirect di TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f2509e7629898b0ad6323dc40be147d617e5f70d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174864"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Salvare dati con i metodi DBDirect di TableAdapter
Questa procedura dettagliata vengono fornite istruzioni dettagliate per l'esecuzione di istruzioni SQL direttamente su un database utilizzando i metodi DBDirect di un oggetto TableAdapter. I metodi DBDirect di un oggetto TableAdapter forniscono un elevato livello di controllo degli aggiornamenti del database. È possibile utilizzarli per eseguire istruzioni SQL specifiche e stored procedure chiamando i singoli `Insert`, `Update`, e `Delete` metodi secondo le esigenze dell'applicazione (a differenza di overload `Update` metodo che esegue l'aggiornamento INSERT e istruzioni di eliminazione in un'unica chiamata).

 Durante questa procedura dettagliata, si apprenderà come:

-   Creare una nuova **Windows Forms Application**.

-   Creare e configurare un set di dati con il [configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).

-   Selezionare il controllo da creare nel form quando si trascinano elementi dal **Zdroje dat** finestra. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Creare un form con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.

-   Aggiungere i metodi per accedere al database ed eseguire gli inserimenti, aggiornamenti ed eliminazioni direttamente.

## <a name="prerequisites"></a>Prerequisiti
Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Form
 Il primo passaggio consiste nel creare un **Windows Forms Application**.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **TableAdapterDbDirectMethodsWalkthrough**, quindi scegliere **OK**.

     Il **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto al progetto **Esplora soluzioni**.

## <a name="create-a-data-source-from-your-database"></a>Creare un'origine dati dal database
 Questo passaggio Usa la **configurazione guidata origine dati** per creare un'origine dati basata sul `Region` tabella nel database di esempio Northwind. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione del database di esempio Northwind, vedere [procedura: installare database di esempio](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1.  Nel **Data** dal menu **Mostra origini dati**.

2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.

3.  Nel **scegliere un tipo di origine dati** schermata, seleziona **Database**e quindi selezionare **Next**.

4.  Nel **scegliere la connessione dati** schermata, effettuare una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         oppure

    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **successivo**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** schermata, seleziona **successivo**.

7.  Nel **Scegli oggetti di Database** schermata, quindi espandere il **tabelle** nodo.

8.  Selezionare il `Region` tabella e quindi selezionare **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e il `Region` inclusa nella tabella di **Zdroje dat** finestra.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Aggiungere controlli al form per visualizzare i dati
 Creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare dati associati a controlli nel form di Windows

-   Trascinare l'oggetto principale **regione** nodo dal **Zdroje dat** finestra nei form.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter

1.  Trascinare tre <xref:System.Windows.Forms.Button> dei controlli il **casella degli strumenti** nello **Form1** (sotto la **RegionDataGridView**).

2.  Impostare le opzioni seguenti **Name** e **testo** le proprietà per ogni pulsante.

    |nome|Testo|
    |----------|----------|
    |`InsertButton`|**Inserisci**|
    |`UpdateButton`|**Aggiornamento**|
    |`DeleteButton`|**Eliminazione**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Per aggiungere il codice per l'inserimento dei nuovi record nel database

1.  Selezionare **InsertButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.

2.  Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Per aggiungere il codice per l'aggiornamento dei record nel database

1.  Fare doppio clic il **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.

2.  Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Per aggiungere il codice per eliminare record dal database

1.  Selezionare **DeleteButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor del codice.

2.  Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Esecuzione dell'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

-   Selezionare **F5** per eseguire l'applicazione.

-   Selezionare il **Inserisci** pulsante e verificare che il nuovo record venga visualizzato nella griglia.

-   Selezionare il **Update** pulsante e verificare che il record viene aggiornato nella griglia.

-   Selezionare il **eliminare** pulsante e verificare che il record viene rimosso dalla griglia.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, sono disponibili diversi passaggi, che si potrebbe voler eseguire dopo la creazione di un form con associazione a dati. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Aggiunta di funzionalità di ricerca al form.

-   Aggiunta di altre tabelle al set di dati selezionando **configura il DataSet con Creazione guidata** dall'interno di **Zdroje dat** finestra. È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)