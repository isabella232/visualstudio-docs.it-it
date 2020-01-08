---
title: Oggetti personalizzati di associazione dati
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 09e3ad2cfc2690c27e4e26e51f6b40d7afd79f54
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586991"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Associare oggetti come origini dati in Visual Studio

Visual Studio offre strumenti in fase di progettazione per l'utilizzo di oggetti personalizzati come origine dati nell'applicazione. Quando si desidera archiviare i dati da un database in un oggetto associato ai controlli dell'interfaccia utente, l'approccio consigliato consiste nell'utilizzare Entity Framework per generare la classe o le classi. Entity Framework genera automaticamente tutto il codice di rilevamento delle modifiche standard, il che significa che tutte le modifiche apportate agli oggetti locali vengono rese automaticamente permanente nel database quando si chiama AcceptChanges nell'oggetto DbSet. Per ulteriori informazioni, vedere [Entity Framework documentazione](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Gli approcci all'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basata sui set di impostazioni. È anche possibile usare questi approcci se si ha già familiarità con i set di dati e i dati che verranno elaborati sono tabulari e non troppo complessi o troppo grandi. Per un esempio ancora più semplice, che implica il caricamento dei dati direttamente negli oggetti usando un DataReader e l'aggiornamento manuale dell'interfaccia utente senza data binding, vedere [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisiti per gli oggetti

L'unico requisito per usare gli oggetti personalizzati con gli strumenti di progettazione dei dati in Visual Studio è che l'oggetto necessita almeno di una proprietà pubblica.

In genere, gli oggetti personalizzati non richiedono interfacce, costruttori o attributi specifici che fungano da origine dati per un'applicazione. Tuttavia, se si desidera trascinare l'oggetto dalla finestra **origini dati** in un'area di progettazione per creare un controllo con associazione a dati e se l'oggetto implementa l'interfaccia <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource>, l'oggetto deve disporre di un costruttore predefinito. In caso contrario, Visual Studio non è in grado di creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati

Sebbene esistano innumerevoli modi per implementare la logica dell'applicazione quando si utilizzano oggetti come origine dati, per i database SQL sono disponibili alcune operazioni standard che possono essere semplificate tramite gli oggetti TableAdapter generati da Visual Studio. In questa pagina viene illustrato come implementare questi processi standard utilizzando oggetti TableAdapter. Non viene utilizzato come guida per la creazione di oggetti personalizzati. Ad esempio, si eseguono in genere le operazioni standard seguenti indipendentemente dall'implementazione specifica degli oggetti o dalla logica dell'applicazione:

- Caricamento dei dati in oggetti, in genere da un database.

- Creazione di una raccolta tipizzata di oggetti.

- Aggiunta e rimozione di oggetti da una raccolta.

- Visualizzazione dei dati oggetto per gli utenti in un form.

- Modifica o modifica dei dati in un oggetto.

- Salvataggio di dati dagli oggetti di nuovo nel database.

### <a name="load-data-into-objects"></a>Caricare i dati in oggetti

Per questo esempio, si caricano i dati negli oggetti usando TableAdapter. Per impostazione predefinita, gli oggetti TableAdapter vengono creati con due tipi di metodi che recuperano dati da un database e popolano le tabelle di dati.

- Il metodo `TableAdapter.Fill` compila una tabella dati esistente con i dati restituiti.

- Il metodo `TableAdapter.GetData` restituisce una nuova tabella dati popolata con i dati.

Il modo più semplice per caricare gli oggetti personalizzati con dati consiste nel chiamare il metodo `TableAdapter.GetData`, eseguire il ciclo della raccolta di righe nella tabella dati restituita e popolare ogni oggetto con i valori in ogni riga. È possibile creare un metodo di `GetData` che restituisca una tabella dati popolata per qualsiasi query aggiunta a un TableAdapter.

> [!NOTE]
> Visual Studio denomina le query TableAdapter `Fill` e `GetData` per impostazione predefinita, ma è possibile modificare tali nomi in qualsiasi nome di metodo valido.

Nell'esempio seguente viene illustrato come eseguire il ciclo delle righe in una tabella di dati e compilare un oggetto con i dati:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Creare una raccolta tipizzata di oggetti

È possibile creare classi di raccolte per gli oggetti oppure utilizzare le raccolte tipizzate fornite automaticamente dal [componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component).

Quando si crea una classe di raccolta personalizzata per gli oggetti, è consigliabile ereditare da <xref:System.ComponentModel.BindingList%601>. Questa classe generica fornisce funzionalità per l'amministrazione della raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di associazione dati in Windows Forms.

La raccolta generata automaticamente nell'<xref:System.Windows.Forms.BindingSource> utilizza un <xref:System.ComponentModel.BindingList%601> per la raccolta tipizzata. Se l'applicazione non richiede funzionalità aggiuntive, è possibile gestire la raccolta all'interno del <xref:System.Windows.Forms.BindingSource>. Per ulteriori informazioni, vedere la proprietà <xref:System.Windows.Forms.BindingSource.List%2A> della classe <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Se per la raccolta è richiesta la funzionalità non fornita dall'implementazione di base del <xref:System.ComponentModel.BindingList%601>, è necessario creare una raccolta personalizzata, in modo da poterla aggiungere alla classe in base alle esigenze.

Nel codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzata di oggetti `Order`:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Aggiungere oggetti a una raccolta

Per aggiungere oggetti a una raccolta, chiamare il metodo `Add` della classe di raccolta personalizzata o del <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> Il metodo `Add` viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.

Nel codice seguente viene illustrato come aggiungere oggetti alla raccolta tipizzata in un <xref:System.Windows.Forms.BindingSource>:

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

Nel codice seguente viene illustrato come aggiungere oggetti a una raccolta tipizzata che eredita da <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> In questo esempio, la raccolta `Orders` è una proprietà dell'oggetto `Customer`.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Rimuovere oggetti da una raccolta

Per rimuovere oggetti da una raccolta, chiamare il metodo `Remove` o `RemoveAt` della classe di raccolta personalizzata o di <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> I metodi `Remove` e `RemoveAt` vengono forniti automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601>.

Nel codice seguente viene illustrato come individuare e rimuovere oggetti dalla raccolta tipizzata in una <xref:System.Windows.Forms.BindingSource> con il metodo <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Visualizza dati oggetto agli utenti

Per visualizzare i dati negli oggetti per gli utenti, creare un'origine dati oggetto utilizzando la **Configurazione guidata origine dati** , quindi trascinare l'intero oggetto o le singole proprietà nel form dalla finestra **origini dati** .

### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti

Per modificare i dati in oggetti personalizzati che sono associati a dati a controlli di Windows Forms, è sufficiente modificare i dati nel controllo associato (o direttamente nelle proprietà dell'oggetto). L'architettura di data binding aggiorna i dati nell'oggetto.

Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi di come le tabelle dati tengono traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>e <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Salvare i dati negli oggetti di nuovo nel database

Salvare nuovamente i dati nel database passando i valori dall'oggetto ai metodi DBDirect del TableAdapter.

Visual Studio crea metodi DBDirect che possono essere eseguiti direttamente sul database. Questi metodi non richiedono oggetti DataSet o DataTable.

|Metodo DBDirect di TableAdapter|Descrizione|
| - |-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database, consentendo di passare i singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo Update accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il metodo `TableAdapter.Update` viene inoltre usato per riconciliare le modifiche in un set di dati nel database, accettando una <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>o una matrice di <xref:System.Data.DataRow>s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

Per salvare i dati da una raccolta di oggetti, eseguire il ciclo della raccolta di oggetti, ad esempio usando un ciclo for-Next. Inviare i valori per ogni oggetto al database usando i metodi DBDirect del TableAdapter.

Nell'esempio seguente viene illustrato come utilizzare il metodo `TableAdapter.Insert` DBDirect per aggiungere un nuovo cliente direttamente nel database:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Vedere anche

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
