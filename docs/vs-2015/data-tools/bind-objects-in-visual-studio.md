---
title: Oggetti bind
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c487df5623a233146655593265e15c34a884de3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673001"
---
# <a name="bind-objects-in-visual-studio"></a>Associare oggetti in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio offre strumenti in fase di progettazione per l'utilizzo di oggetti personalizzati come origine dati nell'applicazione. Quando si desidera archiviare i dati da un database in un oggetto associato ai controlli dell'interfaccia utente, l'approccio consigliato consiste nell'utilizzare Entity Framework per generare la classe o le classi. L'entità Frameworkautogenerates tutto il codice del rilevamento delle modifiche standard, il che significa che tutte le modifiche apportate agli oggetti locali vengono rese automaticamente permanente nel database quando si chiama AcceptChanges nell'oggetto DbSet.    Per ulteriori informazioni, vedere [Entity Framework documentazione](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Gli approcci all'associazione di oggetti in questo articolo devono essere considerati solo se l'applicazione è già basata sui set di impostazioni. Questi approcci possono anche essere usati se si ha già familiarità con i set di dati e i dati da elaborare sono tabulari e non troppo complessi o troppo grandi. Per un esempio ancora più semplice, che implica il caricamento dei dati direttamente negli oggetti usando un DataReader e l'aggiornamento manuale dell'interfaccia utente senza data binding, vedere [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisiti per gli oggetti
 L'unico requisito per usare gli oggetti personalizzati con gli strumenti di progettazione dei dati in Visual Studio è che l'oggetto necessita almeno di una proprietà pubblica.

 In genere, gli oggetti personalizzati non richiedono interfacce, costruttori o attributi specifici che fungano da origine dati per un'applicazione. Tuttavia, se si desidera trascinare l'oggetto dalla finestra **origini dati** in un'area di progettazione per creare un controllo con associazione a dati e se l'oggetto implementa l' <xref:System.ComponentModel.ITypedList> interfaccia o <xref:System.ComponentModel.IListSource> , l'oggetto deve disporre di un costruttore predefinito. In caso contrario, Visual Studio non è in grado di creare un'istanza dell'oggetto origine dati e viene visualizzato un errore quando si trascina l'elemento nell'area di progettazione.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Esempi di utilizzo di oggetti personalizzati come origini dati
 Sebbene esistano innumerevoli modi per implementare la logica dell'applicazione quando si utilizzano oggetti come origine dati, per i database SQL sono disponibili alcune operazioni standard che possono essere semplificate tramite gli oggetti TableAdapter generati da Visual Studio. Questa pagina illustra come implementare questi processi standard usando TableAdapters.It non è una guida per la creazione di oggetti personalizzati. Ad esempio, si eseguono in genere le operazioni standard seguenti indipendentemente dall'implementazione specifica degli oggetti o dalla logica dell'applicazione:

- Caricamento dei dati in oggetti, in genere da un database.

- Creazione di una raccolta tipizzata di oggetti.

- Aggiunta e rimozione di oggetti da una raccolta.

- Visualizzazione dei dati oggetto per gli utenti in un form.

- Modifica o modifica dei dati in un oggetto.

- Salvataggio di dati dagli oggetti di nuovo nel database.

> [!NOTE]
> Per comprendere meglio e fornire il contesto per gli esempi in questa pagina, è consigliabile completare le operazioni seguenti: [procedura dettagliata: connessione ai dati in oggetti (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). Questa procedura dettagliata crea gli oggetti descritti qui.

### <a name="loaddata-into-objects"></a>LoadData in oggetti
 Per questo esempio, si caricano i dati negli oggetti usando TableAdapter. Per impostazione predefinita, gli oggetti TableAdapter vengono creati con due tipi di metodi che recuperano dati da un database e popolano le tabelle di dati.

- Il `TableAdapter.Fill` metodo compila una tabella dati esistente con i dati restituiti.

- Il `TableAdapter.GetData` metodo restituisce una nuova tabella dati popolata con i dati.

  Il modo più semplice per caricare gli oggetti personalizzati con dati consiste nel chiamare il `TableAdapter.GetData` metodo, eseguire il ciclo della raccolta di righe nella tabella dati restituita e popolare ogni oggetto con i valori in ogni riga. È possibile creare un `GetData` metodo che restituisca una tabella dati popolata per qualsiasi query aggiunta a un TableAdapter.

> [!NOTE]
> Visual Studio denomina le query TableAdapter `Fill` e per `GetData` impostazione predefinita, ma tali nomi possono essere modificati in qualsiasi nome di metodo valido.

 Nell'esempio seguente viene illustrato come eseguire il ciclo delle righe in una tabella di dati e compilare un oggetto con i dati:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Creare una raccolta tipizzata di oggetti
 È possibile creare classi di raccolte per gli oggetti oppure utilizzare le raccolte tipizzate fornite automaticamente dal [componente BindingSource](https://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Quando si crea una classe di raccolta personalizzata per gli oggetti, è consigliabile ereditare da <xref:System.ComponentModel.BindingList%601> . Questa classe generica fornisce funzionalità per l'amministrazione della raccolta, nonché la possibilità di generare eventi che inviano notifiche all'infrastruttura di associazione dati in Windows Forms.

 La raccolta generata automaticamente in <xref:System.Windows.Forms.BindingSource> Usa un oggetto <xref:System.ComponentModel.BindingList%601> per la raccolta tipizzata. Se l'applicazione non richiede funzionalità aggiuntive, è possibile gestire la raccolta all'interno di <xref:System.Windows.Forms.BindingSource> . Per ulteriori informazioni, vedere la <xref:System.Windows.Forms.BindingSource.List%2A> proprietà della <xref:System.Windows.Forms.BindingSource> classe.

> [!NOTE]
> Se per la raccolta è richiesta la funzionalità non fornita dall'implementazione di base di <xref:System.ComponentModel.BindingList%601> , è necessario creare una raccolta personalizzata in modo che sia possibile aggiungerla alla classe in base alle esigenze.

 Nel codice seguente viene illustrato come creare la classe per una raccolta fortemente tipizzata di `Order` oggetti:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>AddObjects a una raccolta
 Per aggiungere oggetti a una raccolta, chiamare il `Add` metodo della classe di raccolta personalizzata o di <xref:System.Windows.Forms.BindingSource> .

 Per un esempio di aggiunta a una raccolta usando un oggetto <xref:System.Windows.Forms.BindingSource> , vedere il `LoadCustomers` metodo in [procedura dettagliata: connessione ai dati in oggetti (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Per un esempio di aggiunta di oggetti a una raccolta personalizzata, vedere il `LoadOrders` metodo in [procedura dettagliata: connessione ai dati in oggetti (Windows Forms)](https://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> Il `Add` metodo viene fornito automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

 Nel codice seguente viene illustrato come aggiungere oggetti alla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource> :

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 Nel codice seguente viene illustrato come aggiungere oggetti a una raccolta tipizzata che eredita da <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> In questo esempio la `Orders` raccolta è una proprietà dell' `Customer` oggetto.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Removeobjects da una raccolta
 Per rimuovere oggetti da una raccolta, chiamare il `Remove` `RemoveAt` metodo o della classe di raccolta personalizzata o di <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> I `Remove` `RemoveAt` metodi e vengono forniti automaticamente per la raccolta personalizzata quando si eredita da <xref:System.ComponentModel.BindingList%601> .

 Nel codice seguente viene illustrato come individuare e rimuovere oggetti dalla raccolta tipizzata in un oggetto <xref:System.Windows.Forms.BindingSource> con il <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> Metodo:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>DisplayObject i dati agli utenti
 Per visualizzare i dati negli oggetti per gli utenti, creare un'origine dati oggetto utilizzando la **Configurazione guidata origine dati** , quindi trascinare l'intero oggetto o le singole proprietà nel form dalla finestra **origini dati** .

### <a name="modify-the-data-in-objects"></a>Modificare i dati negli oggetti
 Per modificare i dati in oggetti personalizzati che sono associati a dati a controlli di Windows Forms, è sufficiente modificare i dati nel controllo associato (o direttamente nelle proprietà dell'oggetto). L'architettura di data binding aggiorna i dati nell'oggetto.

 Se l'applicazione richiede il rilevamento delle modifiche e il rollback delle modifiche proposte ai valori originali, è necessario implementare questa funzionalità nel modello a oggetti. Per esempi di come le tabelle dati tengono traccia delle modifiche proposte, vedere <xref:System.Data.DataRowState> , <xref:System.Data.DataSet.HasChanges%2A> e <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData negli oggetti di nuovo nel database
 Salvare nuovamente i dati nel database passando i valori dall'oggetto ai metodi DBDirect del TableAdapter.

 Visual Studio crea metodi DBDirect che possono essere eseguiti direttamente sul database. Questi metodi non richiedono oggetti DataSet o DataTable.

|Metodo DBDirect di TableAdapter|Descrizione|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Aggiunge nuovi record a un database, consentendo di passare i singoli valori di colonna come parametri del metodo.|
|`TableAdapter.Update`|Aggiorna i record esistenti in un database. Il metodo Update accetta i valori di colonna originali e nuovi come parametri del metodo. I valori originali vengono usati per individuare il record originale e i nuovi valori vengono usati per aggiornare il record.<br /><br /> Il `TableAdapter.Update` metodo viene inoltre usato per riconciliare le modifiche in un set di dati nel database, accettando una <xref:System.Data.DataSet> matrice,, <xref:System.Data.DataTable> <xref:System.Data.DataRow> o di <xref:System.Data.DataRow> s come parametri del metodo.|
|`TableAdapter.Delete`|Elimina i record esistenti dal database in base ai valori di colonna originali passati come parametri del metodo.|

 Per salvare i dati da una raccolta di oggetti, eseguire il ciclo della raccolta di oggetti, ad esempio usando un ciclo for-Next. Inviare i valori per ogni oggetto al database usando i metodi DBDirect del TableAdapter.

 Nell'esempio seguente viene illustrato come utilizzare il `TableAdapter.Insert` metodo DBDirect per aggiungere un nuovo cliente direttamente nel database:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Vedere anche
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
