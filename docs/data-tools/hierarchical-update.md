---
title: Aggiornamento gerarchico
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 158908c45d33781bc9f983950d5558a23481ad37
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586575"
---
# <a name="hierarchical-update"></a>Aggiornamento gerarchico

L' *aggiornamento gerarchico* si riferisce al processo di salvataggio dei dati aggiornati (da un set di dati con due o più tabelle correlate) a un database mantenendo le regole di integrità referenziale. L' *integrità referenziale* si riferisce alle regole di coerenza fornite dai vincoli in un database che controllano il comportamento di inserimento, aggiornamento ed eliminazione di record correlati. Ad esempio, è l'integrità referenziale che impone la creazione di un record del cliente prima di consentire la creazione degli ordini per quel cliente.  Per ulteriori informazioni sulle relazioni nei set di dati, vedere [relazioni nei set](../data-tools/relationships-in-datasets.md)di dati.

La funzionalità di aggiornamento gerarchico usa un `TableAdapterManager` per gestire le `TableAdapter`in un set di dati tipizzato. Il componente `TableAdapterManager` è una classe generata da Visual Studio, non un tipo .NET. Quando si trascina una tabella dalla finestra **origini dati** a una pagina Windows Form o WPF, Visual Studio aggiunge una variabile di tipo TableAdapterManager al form o alla pagina, che viene visualizzata nella barra dei componenti della finestra di progettazione. Per informazioni dettagliate sulla classe `TableAdapterManager`, vedere la sezione di riferimento TableAdapterManager degli [oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

Per impostazione predefinita, un set di dati considera le tabelle correlate come "solo relazioni", il che significa che non impone vincoli di chiave esterna. È possibile modificare tale impostazione in fase di progettazione utilizzando il **Progettazione DataSet**. Selezionare la linea di relazione tra due tabelle per visualizzare la finestra di dialogo **relazione** . Le modifiche apportate in questo articolo determineranno il comportamento del `TableAdapterManager` quando invierà le modifiche nelle tabelle correlate al database.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Abilitare l'aggiornamento gerarchico in un set di dati

Per impostazione predefinita, l'aggiornamento gerarchico è abilitato per tutti i nuovi set di impostazioni aggiunti o creati in un progetto. Attivare o disattivare l'aggiornamento gerarchico impostando la proprietà di **aggiornamento gerarchico** di un set di dati tipizzato nel set di dati su **true** o **false**:

![Impostazione di aggiornamento gerarchico](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Crea una nuova relazione tra le tabelle

Per creare una nuova relazione tra due tabelle, nella Progettazione DataSet selezionare la barra del titolo di ogni tabella, quindi fare clic con il pulsante destro del mouse e scegliere **Aggiungi relazione**.

![Menu Aggiungi relazione di aggiornamento gerarchico](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Informazioni sui vincoli di chiave esterna, sugli aggiornamenti a catena e sulle eliminazioni

È importante comprendere come vengono creati i vincoli di chiave esterna e il comportamento a catena nel database nel codice del set di dati generato.

Per impostazione predefinita, le tabelle di dati in un set di dati vengono generate con relazioni (<xref:System.Data.DataRelation>) che corrispondono alle relazioni nel database. Tuttavia, la relazione nel set di dati non viene generata come vincolo di chiave esterna. Il <xref:System.Data.DataRelation> è configurato come **relazione solo** senza <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> o <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> in vigore.

Per impostazione predefinita, gli aggiornamenti a catena e le eliminazioni a cascata sono spenti anche se la relazione di database è impostata con aggiornamenti a cascata e/o eliminazioni a cascata accese. Se ad esempio si crea un nuovo cliente e un nuovo ordine e si tenta di salvare i dati, è possibile che si verifichi un conflitto con i vincoli di chiave esterna definiti nel database. Per altre informazioni, vedere [disabilitare i vincoli durante il riempimento di un set di dati](turn-off-constraints-while-filling-a-dataset.md).

## <a name="set-the-order-to-perform-updates"></a>Imposta l'ordine di esecuzione degli aggiornamenti

Impostando l'ordine di esecuzione degli aggiornamenti, viene impostato l'ordine dei singoli inserimenti, aggiornamenti ed eliminazioni necessari per salvare tutti i dati modificati in tutte le tabelle di un set di dati. Quando è abilitato l'aggiornamento gerarchico, vengono eseguiti prima gli inserimenti, quindi vengono aggiornati e quindi eliminati. Il `TableAdapterManager` fornisce una proprietà `UpdateOrder` che può essere impostata per eseguire prima gli aggiornamenti, quindi inserisce e quindi Elimina.

> [!NOTE]
> È importante comprendere che l'ordine di aggiornamento è incluso. Ovvero, quando vengono eseguiti gli aggiornamenti, le operazioni di inserimento e di eliminazione vengono eseguite per tutte le tabelle nel set di dati.

Per impostare la proprietà `UpdateOrder`, dopo aver trascinato gli elementi dalla [finestra Origini dati](add-new-data-sources.md#data-sources-window) in un modulo, selezionare il `TableAdapterManager` nella barra dei componenti, quindi impostare la proprietà `UpdateOrder` nella finestra **Proprietà** .

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Creare una copia di backup di un set di dati prima di eseguire un aggiornamento gerarchico

Quando si salvano i dati (chiamando il metodo `TableAdapterManager.UpdateAll()`), il `TableAdapterManager` tenta di aggiornare i dati per ogni tabella in una singola transazione. Se una parte dell'aggiornamento per una tabella ha esito negativo, viene eseguito il rollback dell'intera transazione. Nella maggior parte dei casi, il rollback restituisce l'applicazione allo stato originale.

Tuttavia, a volte potrebbe essere necessario ripristinare il set di dati dalla copia di backup. Un esempio può verificarsi quando si usano valori di incremento automatico. Se, ad esempio, un'operazione di salvataggio ha esito negativo, i valori di incremento automatico non vengono reimpostati nel set di dati e il set di dati continua a creare valori con incremento automatico. In questo modo si lascia un divario di numerazione che potrebbe non essere accettabile nell'applicazione. In situazioni in cui questo è un problema, il `TableAdapterManager` fornisce una proprietà `BackupDataSetBeforeUpdate` che sostituisce il set di dati esistente con una copia di backup in caso di errore della transazione.

> [!NOTE]
> La copia di backup è presente solo in memoria mentre è in esecuzione il metodo `TableAdapterManager.UpdateAll`. Pertanto, non esiste alcun accesso programmatico a questo set di dati di backup perché sostituisce il set di dati originale o esce dall'ambito non appena termina l'esecuzione del `TableAdapterManager.UpdateAll` metodo.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificare il codice di salvataggio generato per eseguire l'aggiornamento gerarchico

Salvare le modifiche dalle tabelle dati correlate del set di dati nel database chiamando il metodo `TableAdapterManager.UpdateAll` e passando il nome del set di dati contenente le tabelle correlate. Ad esempio, eseguire il metodo `TableAdapterManager.UpdateAll(NorthwindDataset)` per inviare gli aggiornamenti da tutte le tabelle presenti in NorthwindDataSet al database back-end.

Dopo avere rilasciato gli elementi dalla finestra **Origini dati**, il codice viene automaticamente aggiunto all'evento `Form_Load` per popolare ogni tabella (metodi `TableAdapter.Fill`). Il codice viene anche aggiunto all'evento Click del pulsante **Salva** di <xref:System.Windows.Forms.BindingNavigator> per salvare i dati dal set di dati nel database (metodo `TableAdapterManager.UpdateAll`).

Il codice di salvataggio generato contiene anche una riga di codice che chiama il metodo `CustomersBindingSource.EndEdit`. In particolare, viene chiamato il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> della prima <xref:System.Windows.Forms.BindingSource>aggiunta al modulo. In altre parole, questo codice viene generato solo per la prima tabella trascinata dalla finestra **origini dati** nel form. La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

> [!NOTE]
> Il **Progettazione DataSet** aggiunge solo il codice `BindingSource.EndEdit` per la prima tabella rilasciata nel form. Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo `BindingSource.EndEdit` per ogni tabella correlata nel form. Per questa procedura dettagliata, è necessario quindi aggiungere una chiamata al metodo `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Per aggiornare il codice in modo da eseguire il commit delle modifiche apportate alle tabelle correlate prima del salvataggio

1. Fare doppio clic sul pulsante **Salva** in <xref:System.Windows.Forms.BindingNavigator> per aprire **Form1** nell'editor del codice.

2. Aggiungere una riga di codice per chiamare il metodo `OrdersBindingSource.EndEdit` dopo la riga che chiama il metodo `CustomersBindingSource.EndEdit`. Il codice nell'evento Click del pulsante **Salva** deve essere simile al seguente:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Oltre a eseguire il commit delle modifiche apportate a una tabella figlio correlata prima di salvare i dati in un database, potrebbe anche essere necessario eseguire il commit dei record padre appena creati prima di aggiungere i nuovi record figlio in un set di dati. In altre parole, potrebbe essere necessario aggiungere il nuovo record padre (`Customer`) al set di dati prima che i vincoli di chiave esterna consentano l'aggiunta di nuovi record figlio (`Orders`) al set di dati. A tale scopo, è possibile usare l'evento figlio `BindingSource.AddingNew`.

> [!NOTE]
> La possibilità di eseguire il commit di nuovi record padre dipende dal tipo di controllo utilizzato per l'associazione all'origine dati. In questa procedura dettagliata vengono usati singoli controlli per eseguire il binding alla tabella padre. Questa operazione richiede il codice aggiuntivo per eseguire il commit del nuovo record padre. Se i record padre venivano invece visualizzati in un controllo di binding complesso come il <xref:System.Windows.Forms.DataGridView>, questa chiamata <xref:System.Windows.Forms.BindingSource.EndEdit%2A> aggiuntiva per il record padre non sarebbe necessaria. perché la funzionalità di data-binding sottostante del controllo gestisce l'esecuzione del commit dei nuovi record.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Per aggiungere il codice per eseguire il commit dei record padre nel set di dati prima dell'aggiunta dei nuovi record figlio

1. Creare un gestore eventi per l'evento `OrdersBindingSource.AddingNew`.

    - Aprire **Form1** nella visualizzazione progettazione, selezionare **OrdersBindingSource** nella barra dei componenti, selezionare **eventi** nella finestra **Proprietà** , quindi fare doppio clic sull'evento **AddingNew** .

2. Aggiungere una riga di codice al gestore eventi che chiama il metodo `CustomersBindingSource.EndEdit`. Il codice nel gestore eventi `OrdersBindingSource_AddingNew` deve essere simile al seguente:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Riferimento a TableAdapterManager

Per impostazione predefinita, quando si crea un set di dati contenente tabelle correlate viene generata una classe `TableAdapterManager`. Per impedire la generazione della classe, modificare il valore della proprietà `Hierarchical Update` del set di dati in false. Quando si trascina una tabella con una relazione nell'area di progettazione di una pagina Windows Form o WPF, Visual Studio dichiara una variabile membro della classe. Se non si usa l'associazione dati, è necessario dichiarare manualmente la variabile.

La classe `TableAdapterManager` non è un tipo .NET. Pertanto, non è possibile cercarlo nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.

Di seguito sono riportati i metodi e le proprietà di uso frequente della classe `TableAdapterManager`:

|Member|Descrizione|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati di tutte le tabelle di dati.|
|Proprietà`BackUpDataSetBeforeUpdate`|Determina se creare una copia di backup del set di dati prima di eseguire il metodo `TableAdapterManager.UpdateAll`. Boolean.|
|proprietà *tablename* `TableAdapter`|Rappresenta un `TableAdapter`. Il `TableAdapterManager` generato contiene una proprietà per ogni `TableAdapter` gestito. Ad esempio, un set di dati con una tabella Customers e Orders viene generato con un `TableAdapterManager` contenente `CustomersTableAdapter` e `OrdersTableAdapter` proprietà.|
|Proprietà`UpdateOrder`|Controlla l'ordine dei singoli comandi INSERT, Update e DELETE. Impostare questa impostazione su uno dei valori nell'enumerazione `TableAdapterManager.UpdateOrderOption`.<br /><br /> Per impostazione predefinita, la `UpdateOrder` è impostata su **InsertUpdateDelete**. Ciò significa che gli inserimenti, gli aggiornamenti e le eliminazioni vengono eseguiti per tutte le tabelle nel set di dati.|

## <a name="see-also"></a>Vedere anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
