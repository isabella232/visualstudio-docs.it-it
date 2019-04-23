---
title: Associa dati di oggetti personalizzati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4fb5a8c7a54871c7d948a458768c5551dbb5d550
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091759"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Associare oggetti come origini dati in Visual Studio

Visual Studio offre gli strumenti di progettazione per l'utilizzo di oggetti personalizzati come origine dei dati nell'applicazione. Quando si desidera archiviare i dati da un database in un oggetto che si associa ai controlli dell'interfaccia utente, l'approccio consigliato è usare Entity Framework per generare le classi. Entity Framework genera automaticamente tutto il rilevamento delle modifiche codice boilerplate, il che significa che tutte le modifiche agli oggetti locali vengono automaticamente resi persistenti nel database quando si chiama AcceptChanges sull'oggetto DbSet. Per altre informazioni, vedere [documentazione di Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Gli approcci per l'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basata su set di dati. È anche possibile usare questi approcci se si ha già familiarità con i set di dati e i dati da elaborare siano tabulare e non troppo complessa o troppo grande. Per un esempio ancora più semplice, che includono il caricamento dei dati direttamente a un oggetto utilizzando un oggetto DataReader e aggiornare manualmente l'interfaccia utente senza l'associazione dati, vedere [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisiti di oggetti

L'unico requisito per gli oggetti personalizzati lavorare con i dati di strumenti di progettazione in Visual Studio è che l'oggetto richiede almeno una proprietà pubblica.

In generale, gli oggetti personalizzati non richiedono qualsiasi interfacce specifiche, i costruttori o attributi a fungere da origine dati per un'applicazione. Tuttavia, se si vuole trascinare l'oggetto dal **Zdroje dat** finestra per un'area di progettazione per creare un controllo con associazione a dati, e se l'oggetto implementa il <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaccia, l'oggetto deve avere un valore predefinito costruttore. In caso contrario, Visual Studio non è possibile creare un'istanza dell'oggetto origine dati e visualizza un errore quando si trascina l'elemento all'area di progettazione.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati

Anche se esistono innumerevoli modalità per implementare la logica dell'applicazione quando si lavora con gli oggetti come origine dati, per SQL database vi sono alcune operazioni standard che possono essere semplificate utilizzando gli oggetti TableAdapter generate Visual Studio. Questa pagina illustra come implementare questi processi standard usando oggetti TableAdapter. Non utilizzo come guida per la creazione di oggetti personalizzati. Ad esempio, è in genere eseguirà le operazioni standard seguente indipendentemente dall'implementazione specifica di oggetti o per la logica dell'applicazione:

- Il caricamento dei dati in oggetti (in genere da un database).

- Creazione di un insieme di oggetti tipizzati.

- Aggiunta e rimozione di oggetti da una raccolta.

- Visualizzazione dati dell'oggetto per gli utenti in un form.

- La modifica o modifica i dati in un oggetto.

- Salvataggio dei dati dagli oggetti nel database.

### <a name="load-data-into-objects"></a>Caricare i dati in oggetti

Per questo esempio, caricare dati in oggetti usando oggetti TableAdapter. Per impostazione predefinita, vengono creati oggetti TableAdapter con due tipi di metodi per recupero i dati da un database e popolano le tabelle di dati.

- Il `TableAdapter.Fill` metodo compila una tabella di dati esistente con i dati restituiti.

- Il `TableAdapter.GetData` metodo restituisce una nuova tabella dati popolata con i dati.

Il modo più semplice per caricare gli oggetti personalizzati con i dati consiste nel chiamare il `TableAdapter.GetData` (metodo), scorrere la raccolta di righe della tabella di dati restituiti in ciclo e popolare ogni oggetto con i valori in ogni riga. È possibile creare un `GetData` metodo che restituisce una tabella dati popolata per le query aggiunte a un oggetto TableAdapter.

> [!NOTE]
> Visual Studio denomina la query TableAdapter `Fill` e `GetData` per impostazione predefinita, ma è possibile modificare questi nomi per qualsiasi nome di metodo valido.

Nell'esempio seguente viene illustrato come scorrere le righe in una tabella dati e popola un oggetto con i dati:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Creare un insieme di oggetti tipizzati

È possibile creare classi di raccolta per gli oggetti o usare le raccolte tipizzate vengono automaticamente fornite per il [componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Quando si crea una classe di raccolta personalizzato per gli oggetti, si consiglia di ereditare da <xref:System.ComponentModel.BindingList%601>. Questa classe generica fornisce funzionalità per gestire la raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di data binding in Windows Form.

La raccolta generata automaticamente nel <xref:System.Windows.Forms.BindingSource> Usa un <xref:System.ComponentModel.BindingList%601> per la relativa raccolta tipizzata. Se l'applicazione richiede funzionalità aggiuntive, è possibile mantenere l'insieme all'interno di <xref:System.Windows.Forms.BindingSource>. Per altre informazioni, vedere la <xref:System.Windows.Forms.BindingSource.List%2A> proprietà del <xref:System.Windows.Forms.BindingSource> classe.

> [!NOTE]
> Se la raccolta richiede funzionalità non fornite dall'implementazione di base del <xref:System.ComponentModel.BindingList%601>, è necessario creare una raccolta personalizzata, è possibile aggiungere alla classe di base alle esigenze.

Il codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzata di `Order` oggetti:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Aggiungere gli oggetti a una raccolta

Per aggiungere oggetti a una raccolta, chiamare il `Add` metodo di una classe di insiemi personalizzati o del <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Il `Add` metodo viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.

Il codice seguente viene illustrato come aggiungere gli oggetti nella raccolta tipizzata in una <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 Il codice seguente viene illustrato come aggiungere gli oggetti in una raccolta tipizzata che eredita da <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> In questo esempio, il `Orders` raccolta è una proprietà del `Customer` oggetto.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Rimuovere gli oggetti da una raccolta

Rimuovere gli oggetti da una raccolta chiamando il `Remove` oppure `RemoveAt` metodo della classe di insiemi personalizzati o di <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Il `Remove` e `RemoveAt` metodi vengono forniti automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.

Il codice seguente viene illustrato come individuare e rimuovere gli oggetti dalla raccolta tipizzata in una <xref:System.Windows.Forms.BindingSource> con il <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> metodo:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Visualizzare i dati oggetto per gli utenti

Per visualizzare i dati negli oggetti agli utenti, creare un'origine dati di oggetti utilizzando il **configurazione dell'origine dati** procedura guidata, quindi trascinare l'intero oggetto o le singole proprietà nel form dal **Zdroje dat**finestra.

### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti

Per modificare i dati in oggetti personalizzati che vengono associati ai controlli Windows Form, è sufficiente modificare i dati nel controllo associato (o direttamente nella proprietà dell'oggetto). Architettura di data binding Aggiorna i dati nell'oggetto.

Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai rispettivi valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi del modo in cui le tabelle di dati tenuta traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, e <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Salvare i dati negli oggetti nel database

Salvare i dati nel database passando i valori dall'oggetto ai metodi DBDirect di TableAdapter.

Visual Studio crea metodi DBDirect di che possono essere eseguiti direttamente sul database. Questi metodi non richiedono oggetti DataSet o DataTable.

|Metodo DBDirect di TableAdapter|Descrizione|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database, consentendo di passare i valori di singole colonne come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record in un database esistenti. Il metodo di aggiornamento richiede valori della colonna originale e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare record in questione.<br /><br /> Il `TableAdapter.Update` metodo viene usato anche per risolvere le modifiche in un set di dati nel database, eseguendo un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matrice di <xref:System.Data.DataRow>s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record dal database in base ai valori di colonna originali passati come parametri del metodo esistenti.|

Per salvare i dati da una raccolta di oggetti, scorrere la raccolta di oggetti (ad esempio, usando un ciclo for next). Inviare i valori per ogni oggetto nel database utilizzando i metodi DBDirect di TableAdapter.

Nell'esempio seguente viene illustrato come utilizzare il `TableAdapter.Insert` DBDirect metodo per aggiungere un nuovo cliente direttamente nel database:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)