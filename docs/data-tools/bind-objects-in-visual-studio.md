---
title: Associazione dati a oggetti personalizzati
description: Associare oggetti come origini dati in Visual Studio. Usare gli strumenti della fase di progettazione per usare oggetti personalizzati come origine dati nell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b837cf77103efa7cf07bdc6f32aabb5028670638
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631595"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Associare oggetti come origini dati in Visual Studio

Visual Studio strumenti in fase di progettazione per l'utilizzo di oggetti personalizzati come origine dati nell'applicazione. Quando si vogliono archiviare dati da un database in un oggetto associato ai controlli dell'interfaccia utente, l'approccio consigliato consiste nell'usare Entity Framework per generare la classe o le classi. Entity Framework genera automaticamente tutto il codice di rilevamento delle modifiche boilerplate, il che significa che tutte le modifiche apportate agli oggetti locali vengono rese automaticamente persistenti nel database quando si chiama AcceptChanges sull'oggetto DbSet. Per altre informazioni, vedere [Entity Framework Documentation](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Gli approcci all'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basata su set di dati. È anche possibile usare questi approcci se si ha già familiarità con i set di dati e i dati che verranno elaborati sono tabulari e non troppo complessi o troppo grandi. Per un esempio ancora più semplice, che prevede il caricamento di dati direttamente in oggetti tramite un DataReader e l'aggiornamento manuale dell'interfaccia utente senza data binding, vedere Creare un'applicazione dati semplice [usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisiti per gli oggetti

L'unico requisito per il funzionamento degli oggetti personalizzati con gli strumenti di progettazione dati in Visual Studio è che l'oggetto necessita di almeno una proprietà pubblica.

In genere, gli oggetti personalizzati non richiedono che interfacce, costruttori o attributi specifici fungono da origine dati per un'applicazione. Tuttavia, se si desidera trascinare  l'oggetto dalla finestra Origini dati in un'area di progettazione per creare un controllo associato a dati e se l'oggetto implementa l'interfaccia o , l'oggetto deve avere un <xref:System.ComponentModel.ITypedList> costruttore <xref:System.ComponentModel.IListSource> predefinito. In caso Visual Studio non è possibile creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati

Anche se esistono moltissimi modi per implementare la logica dell'applicazione quando si usano oggetti come origine dati, per i database SQL esistono alcune operazioni standard che possono essere semplificate usando gli oggetti TableAdapter generati da Visual Studio. Questa pagina illustra come implementare questi processi standard usando TableAdapter. Non è da intendersi come guida per la creazione di oggetti personalizzati. Ad esempio, in genere si eseguono le operazioni standard seguenti indipendentemente dall'implementazione specifica degli oggetti o dalla logica dell'applicazione:

- Caricamento di dati in oggetti (in genere da un database).

- Creazione di una raccolta tipiata di oggetti .

- Aggiunta e rimozione di oggetti da una raccolta.

- Visualizzazione dei dati dell'oggetto agli utenti in un form.

- Modifica o modifica dei dati in un oggetto .

- Salvataggio dei dati dagli oggetti nel database.

### <a name="load-data-into-objects"></a>Caricare dati in oggetti

Per questo esempio, i dati vengono caricati negli oggetti tramite TableAdapter. Per impostazione predefinita, gli oggetti TableAdapter vengono creati con due tipi di metodi che recuperano dati da un database e popolano le tabelle di dati.

- Il `TableAdapter.Fill` metodo riempie una tabella dati esistente con i dati restituiti.

- Il `TableAdapter.GetData` metodo restituisce una nuova tabella di dati popolata con i dati.

Il modo più semplice per caricare gli oggetti personalizzati con i dati è chiamare il metodo , scorrere a ciclo continuo la raccolta di righe nella tabella di dati restituita e popolare ogni oggetto con i valori `TableAdapter.GetData` in ogni riga. È possibile creare un `GetData` metodo che restituisce una tabella di dati popolata per qualsiasi query aggiunta a un oggetto TableAdapter.

> [!NOTE]
> Visual Studio le query TableAdapter e per impostazione predefinita, ma è possibile modificare tali nomi `Fill` con qualsiasi nome di metodo `GetData` valido.

Nell'esempio seguente viene illustrato come scorrere a ciclo continuo le righe di una tabella dati e popolare un oggetto con dati:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb" id="Snippet4":::

### <a name="create-a-typed-collection-of-objects"></a>Creare una raccolta tipiata di oggetti

È possibile creare classi di raccolta per gli oggetti o usare le raccolte tipizzati fornite automaticamente dal [componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Quando si crea una classe di raccolta personalizzata per gli oggetti , è consigliabile ereditare da <xref:System.ComponentModel.BindingList%601> . Questa classe generica fornisce funzionalità per amministrare la raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di data binding in Windows Form.

L'insieme generato automaticamente <xref:System.Windows.Forms.BindingSource> nell'oggetto utilizza <xref:System.ComponentModel.BindingList%601> un oggetto per la raccolta tipiata. Se l'applicazione non richiede funzionalità aggiuntive, è possibile gestire la raccolta all'interno di <xref:System.Windows.Forms.BindingSource> . Per altre informazioni, vedere <xref:System.Windows.Forms.BindingSource.List%2A> la proprietà della classe <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Se la raccolta richiede funzionalità non fornite dall'implementazione di base di , è necessario creare una raccolta personalizzata in modo da poter aggiungere <xref:System.ComponentModel.BindingList%601> alla classe in base alle esigenze.

Nel codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzato di `Order` oggetti :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet8":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet8":::

### <a name="add-objects-to-a-collection"></a>Aggiungere oggetti a una raccolta

Per aggiungere oggetti a una raccolta, chiamare `Add` il metodo della classe di raccolta personalizzata o dell'oggetto <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Il `Add` metodo viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

Nel codice seguente viene illustrato come aggiungere oggetti alla raccolta tipiata in <xref:System.Windows.Forms.BindingSource> un oggetto :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet5":::

Nel codice seguente viene illustrato come aggiungere oggetti a una raccolta tipiata che eredita da <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> In questo esempio la `Orders` raccolta è una proprietà dell'oggetto `Customer` .

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet6":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet6":::

### <a name="remove-objects-from-a-collection"></a>Rimuovere oggetti da una raccolta

Per rimuovere oggetti da una raccolta, chiamare il `Remove` metodo o della classe di raccolta personalizzata o di `RemoveAt` <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> I `Remove` metodi e vengono forniti `RemoveAt` automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

Nel codice seguente viene illustrato come individuare e rimuovere oggetti dalla raccolta tipizzata in un <xref:System.Windows.Forms.BindingSource> oggetto con il metodo <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> :

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs" id="Snippet7":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb" id="Snippet7":::

### <a name="display-object-data-to-users"></a>Visualizzare i dati degli oggetti agli utenti

Per visualizzare i dati negli oggetti agli utenti,  creare un'origine dati oggetto usando la Configurazione guidata origine dati, quindi trascinare l'intero oggetto o le singole proprietà nel form dalla **finestra Origini** dati .

### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti

Per modificare i dati in oggetti personalizzati associati Windows controlli form, è sufficiente modificare i dati nel controllo associato (o direttamente nelle proprietà dell'oggetto). L'architettura di data binding aggiorna i dati nell'oggetto .

Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi di come le tabelle dati tengono traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState> <xref:System.Data.DataSet.HasChanges%2A> , e <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Salvare i dati negli oggetti nel database

Salvare di nuovo i dati nel database passando i valori dall'oggetto ai metodi DBDirect del TableAdapter.

Visual Studio crea metodi DBDirect che possono essere eseguiti direttamente nel database. Questi metodi non richiedono oggetti DataSet o DataTable.

|Metodo DBDirect di TableAdapter|Descrizione|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database, consentendo di passare singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo Update accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il metodo viene usato anche per riconciliare le modifiche in un set di dati nel database, prendendo una matrice , , o di `TableAdapter.Update` <xref:System.Data.DataSet> come parametri del <xref:System.Data.DataTable> <xref:System.Data.DataRow> <xref:System.Data.DataRow> metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

Per salvare i dati da una raccolta di oggetti, scorrere a ciclo continuo la raccolta di oggetti , ad esempio usando un ciclo for-next. Inviare i valori per ogni oggetto al database usando i metodi DBDirect del TableAdapter.

L'esempio seguente illustra come usare il `TableAdapter.Insert` metodo DBDirect per aggiungere un nuovo cliente direttamente nel database:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs" id="Snippet23":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb" id="Snippet23":::

## <a name="see-also"></a>Vedi anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
