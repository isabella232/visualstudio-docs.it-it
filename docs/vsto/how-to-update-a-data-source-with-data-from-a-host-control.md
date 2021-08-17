---
title: "Procedura: Aggiornare un'origine dati con i dati di un controllo host"
description: Informazioni su come associare un controllo host a un'origine dati e aggiornare l'origine dati con le modifiche apportate ai dati nel controllo .
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: d389e4f3e2b8bdf4348508760b6894c0eeaf1ec7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026005"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Procedura: Aggiornare un'origine dati con i dati di un controllo host
  È possibile associare un controllo host a un'origine dati e aggiornare l'origine dati con le modifiche apportate ai dati nel controllo. Questo processo prevede due passaggi principali:

1. Aggiornare l'origine dati in memoria con i dati modificati nel controllo. In genere, l'origine dati in memoria è un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable>o un altro oggetto dati.

2. Aggiornare il database con i dati modificati nell'origine dati in memoria. Ciò è possibile solo se l'origine dati è connessa a un database back-end, ad esempio un database SQL Server o Microsoft Office Access.

   Per altre informazioni sui controlli host e data binding, vedere Panoramica degli elementi host e dei controlli [host](../vsto/host-items-and-host-controls-overview.md) e Associare dati ai controlli [in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aggiornare l'origine dati in memoria
 Per impostazione predefinita, i controlli host che consentono il data binding semplice (ad esempio i controlli contenuto in un documento di Word o un controllo di intervallo denominato in un foglio di lavoro di Excel) non salvano le modifiche all'origine dati in memoria. In altre parole, quando un utente finale modifica un valore in un controllo host e successivamente si sposta dal controllo, il nuovo valore del controllo non viene salvato nell'origine dati.

 Per salvare i dati nell'origine dati, è possibile scrivere codice che consenta di aggiornare l'origine dati in risposta a un evento specifico in fase di esecuzione oppure configurare il controllo in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore nel controllo.

 Non è necessario salvare le modifiche apportate a <xref:Microsoft.Office.Tools.Excel.ListObject> nell'origine dati in memoria. Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ai dati, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> salva automaticamente le modifiche nell'origine dati in memoria senza che sia richiesto codice aggiuntivo.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Per aggiornare l'origine dati in memoria in fase di esecuzione

- Chiamare il metodo <xref:System.Windows.Forms.Binding.WriteValue%2A> dell'oggetto <xref:System.Windows.Forms.Binding> che associa il controllo all'origine dati.

     Nell'esempio seguente le modifiche apportate a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in un foglio di lavoro di Excel vengono salvate nell'origine dati. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet1":::

### <a name="automatically-update-the-in-memory-data-source"></a>Aggiornare automaticamente l'origine dati in memoria
 È anche possibile configurare un controllo in modo da aggiornare automaticamente l'origine dati in memoria. In un progetto a livello di documento, questa operazione può essere eseguita tramite codice o tramite la finestra di progettazione. In un VSTO di componente aggiuntivo è necessario usare il codice.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite codice

1. Usare il sistema . Windows. Modalità Forms.DataSourceUpdateMode.OnPropertyChanged dell'oggetto che associa <xref:System.Windows.Forms.Binding> il controllo all'origine dati. Per aggiornare l'origine dati è possibile procedere in due modi:

   - Per aggiornare l'origine dati quando il controllo viene convalidato, impostare questa proprietà su System. Windows. Forms.DataSourceUpdateMode.OnValidation.

   - Per aggiornare l'origine dati quando il valore della proprietà associata a dati del controllo cambia, impostare questa proprietà su System. Windows. Forms.DataSourceUpdateMode.OnPropertyChanged.

     > [!NOTE]
     > Oggetto System. Windows. L'opzione Forms.DataSourceUpdateMode.OnPropertyChanged non si applica ai controlli host di Word, perché Word non offre notifiche di modifica del documento o del controllo. ma può essere usata per i controlli Windows Form nei documenti di Word.

     L'esempio seguente configura un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore del controllo. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet19":::

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite la finestra di progettazione

1. In Visual Studio, aprire il documento di Word o la cartella di lavoro di Excel nella finestra di progettazione.

2. Fare clic sul controllo desiderato per aggiornare automaticamente l'origine dati.

3. Nella finestra **Proprietà** espandere la proprietà **(DataBindings)** .

4. Accanto alla proprietà **(Avanzate)** fare clic sul pulsante con i puntini di sospensione (![screenshot di VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "Schermata VisualStudioEllipsesButton")).

5. Nella finestra di dialogo **Formattazione e associazione avanzata** fare clic nell'elenco a discesa **Modalità aggiornamento origine dati** e selezionare uno dei valori seguenti:

    - Per aggiornare l'origine dati quando il controllo viene convalidato, selezionare **OnValidation**.

    - Per aggiornare l'origine dati quando si modifica il valore della proprietà del controllo associata ai dati, selezionare **OnPropertyChanged**.

        > [!NOTE]
        > L'opzione **OnPropertyChanged** non si applica ai controlli host di Word perché Word non fornisce notifiche relative alle modifiche al documento o al controllo, ma può essere usata per i controlli Windows Form nei documenti di Word.

6. Chiudere la finestra di dialogo **Formattazione e associazione avanzata** .

## <a name="update-the-database"></a>Aggiornare il database
 Se l'origine dati in memoria è associata a un database, è necessario aggiornare il database in base alle modifiche apportate all'origine dati. Per altre informazioni sull'aggiornamento di un database, vedere Salvare di nuovo i dati nel [database](../data-tools/save-data-back-to-the-database.md)  e [Aggiornare i dati usando un oggetto TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>Per aggiornare il database

1. Chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per il controllo <xref:System.Windows.Forms.BindingSource> .

     L'oggetto <xref:System.Windows.Forms.BindingSource> viene generato automaticamente quando un controllo associato a dati viene aggiunto a un documento o a una cartella di lavoro in fase di progettazione. L'oggetto <xref:System.Windows.Forms.BindingSource> connette il controllo al set di dati tipizzato nel progetto. Per altre informazioni, vedere [Panoramica del componente BindingSource.](/dotnet/framework/winforms/controls/bindingsource-component-overview)

     L'esempio di codice seguente presuppone che il progetto contenga un oggetto <xref:System.Windows.Forms.BindingSource> denominato `customersBindingSource`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet20":::

2. Chiamare il `Update` metodo dell'oggetto TableAdapter generato nel progetto.

     L'oggetto TableAdapter viene generato automaticamente quando si aggiunge un controllo con associazione a dati a un documento o a una cartella di lavoro in fase di progettazione. Il TableAdapter connette il set di dati tipizzato nel progetto al database. Per altre informazioni, vedere [Panoramica di TableAdapter.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

     Nell'esempio di codice seguente si presuppone che sia presente una connessione alla tabella Customers nel database Northwind e che il progetto contenga un oggetto TableAdapter denominato e un set di dati `customersTableAdapter` tipizzato denominato `northwindDataSet` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet21":::

## <a name="see-also"></a>Vedi anche
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
- [Aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Procedura: Scorrere i record di database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Procedura: Popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati da oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Popolare documenti con dati dai servizi](../vsto/how-to-populate-documents-with-data-from-services.md)
