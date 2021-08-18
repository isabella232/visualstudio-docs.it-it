---
title: Aggiornamento gerarchico
description: Esaminare gli aggiornamenti gerarchici, che comportano il salvataggio dei dati aggiornati (da un set di dati con più di 2 tabelle correlate) in un database mantenendo al tempo stesso le regole di integrità referenziale.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 74e96bf3644d57235aff82fb2b0393c1506dd653
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121994"
---
# <a name="hierarchical-update"></a>Aggiornamento gerarchico

*L'aggiornamento* gerarchico si riferisce al processo di salvataggio dei dati aggiornati (da un set di dati con due o più tabelle correlate) in un database mantenendo al tempo stesso le regole di integrità referenziale. *L'integrità* referenziale si riferisce alle regole di coerenza fornite dai vincoli in un database che controllano il comportamento di inserimento, aggiornamento ed eliminazione di record correlati. Ad esempio, è l'integrità referenziale che impone la creazione di un record cliente prima di consentire la creazione di ordini per tale cliente.  Per altre informazioni sulle relazioni nei set di dati, vedere [Relazioni nei set di dati](../data-tools/relationships-in-datasets.md).

La funzionalità di aggiornamento gerarchico usa `TableAdapterManager` un oggetto per gestire gli oggetti in un set di dati `TableAdapter` tipizzato. Il `TableAdapterManager` componente è una Visual Studio generata dall'utente, non un tipo .NET. Quando si trascina una  tabella dalla finestra Origini dati a un form Windows o a una pagina WPF, Visual Studio aggiunge una variabile di tipo TableAdapterManager al form o alla pagina e viene visualizzata nella finestra di progettazione nella barra dei componenti. Per informazioni dettagliate sulla `TableAdapterManager` classe , vedere la sezione TableAdapterManager Reference di [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

Per impostazione predefinita, un set di dati considera le tabelle correlate come "solo relazioni", ovvero non applica vincoli di chiave esterna. È possibile modificare tale impostazione in fase di progettazione usando il Progettazione DataSet **.** Selezionare la linea di relazione tra due tabelle per visualizzare la **finestra di dialogo** Relazione . Le modifiche apportate in questo caso determineranno il comportamento dell'oggetto quando invia le modifiche nelle tabelle `TableAdapterManager` correlate al database.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Abilitare l'aggiornamento gerarchico in un set di dati

Per impostazione predefinita, l'aggiornamento gerarchico è abilitato per tutti i nuovi set di dati aggiunti o creati in un progetto. Attivare o disattivare l'aggiornamento gerarchico impostando la proprietà **Aggiornamento** gerarchico di un set di dati tipizzato in Set di dati su **True** o **False**:

![Impostazione di aggiornamento gerarchico](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Creare una nuova relazione tra tabelle

Per creare una nuova relazione tra due tabelle, nell'Progettazione DataSet selezionare la barra del titolo di ogni tabella, quindi fare clic con il pulsante destro del mouse e scegliere **Aggiungi relazione**.

![Menu Aggiungi relazione aggiornamento gerarchico](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Informazioni sui vincoli di chiave esterna, gli aggiornamenti a catena e le eliminazioni

È importante comprendere come vengono creati i vincoli di chiave esterna e il comportamento a catena nel database nel codice del set di dati generato.

Per impostazione predefinita, le tabelle dati in un set di dati vengono generate con relazioni ( <xref:System.Data.DataRelation> ) che corrispondono alle relazioni nel database. Tuttavia, la relazione nel set di dati non viene generata come vincolo di chiave esterna. <xref:System.Data.DataRelation>l'oggetto è configurato come Solo **relazione** senza o <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> in <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> vigore.

Per impostazione predefinita, gli aggiornamenti a catena e le eliminazioni a catena sono disattivati anche se la relazione di database è impostata con gli aggiornamenti a catena e/o le eliminazioni a catena attivate. Ad esempio, la creazione di un nuovo cliente e un nuovo ordine e il tentativo di salvare i dati possono causare un conflitto con i vincoli di chiave esterna definiti nel database. Per altre informazioni, vedere [Disattivare i vincoli durante il riempimento di un set di dati.](turn-off-constraints-while-filling-a-dataset.md)

## <a name="set-the-order-to-perform-updates"></a>Impostare l'ordine di esecuzione degli aggiornamenti

L'impostazione dell'ordine di esecuzione degli aggiornamenti imposta l'ordine dei singoli inserimenti, aggiornamenti ed eliminazioni necessari per salvare tutti i dati modificati in tutte le tabelle di un set di dati. Quando l'aggiornamento gerarchico è abilitato, vengono eseguiti prima gli inserimenti, quindi gli aggiornamenti e quindi le eliminazioni. Fornisce `TableAdapterManager` una proprietà che può essere `UpdateOrder` impostata per eseguire prima gli aggiornamenti, quindi inserisce ed elimina.

> [!NOTE]
> È importante comprendere che l'ordine di aggiornamento è tutto inclusivo. In altre informazioni, quando vengono eseguiti gli aggiornamenti, vengono eseguiti inserimenti e quindi eliminazioni per tutte le tabelle nel set di dati.

Per impostare la proprietà , dopo aver trascinato gli elementi dalla finestra Origini dati in un form, selezionare nella barra dei componenti e quindi impostare la proprietà `UpdateOrder` nella [](add-new-data-sources.md#data-sources-window) `TableAdapterManager` `UpdateOrder` **finestra** Proprietà .

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Creare una copia di backup di un set di dati prima di eseguire un aggiornamento gerarchico

Quando si salvano i dati chiamando il metodo , tenta di aggiornare i dati `TableAdapterManager.UpdateAll()` per ogni tabella in una singola `TableAdapterManager` transazione. Se una parte qualsiasi dell'aggiornamento per una tabella ha esito negativo, viene eseguito il rollback dell'intera transazione. Nella maggior parte dei casi, il rollback riporta l'applicazione allo stato originale.

In alcuni casi può tuttavia essere necessario ripristinare il set di dati dalla copia di backup. Un esempio di questo problema può verificarsi quando si usano valori con incremento automatico. Ad esempio, se un'operazione di salvataggio non riesce, i valori di incremento automatico non vengono reimpostati nel set di dati e il set di dati continua a creare valori a incremento automatico. Ciò lascia un gap nella numerazione che potrebbe non essere accettabile nell'applicazione. In situazioni in cui si tratta di un problema, fornisce una proprietà che sostituisce il set di dati esistente con una copia di `TableAdapterManager` `BackupDataSetBeforeUpdate` backup se la transazione ha esito negativo.

> [!NOTE]
> La copia di backup è in memoria solo durante `TableAdapterManager.UpdateAll` l'esecuzione del metodo . Pertanto, non esiste alcun accesso a livello di codice a questo set di dati di backup perché sostituisce il set di dati originale o esce dall'ambito non appena il metodo `TableAdapterManager.UpdateAll` termina l'esecuzione.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificare il codice di salvataggio generato per eseguire l'aggiornamento gerarchico

Salvare le modifiche dalle tabelle dati correlate del set di dati nel database chiamando il metodo `TableAdapterManager.UpdateAll` e passando il nome del set di dati contenente le tabelle correlate. Ad esempio, eseguire il metodo `TableAdapterManager.UpdateAll(NorthwindDataset)` per inviare gli aggiornamenti da tutte le tabelle presenti in NorthwindDataSet al database back-end.

Dopo avere rilasciato gli elementi dalla finestra **Origini dati**, il codice viene automaticamente aggiunto all'evento `Form_Load` per popolare ogni tabella (metodi `TableAdapter.Fill`). Il codice viene anche aggiunto all'evento Click del pulsante **Salva** di <xref:System.Windows.Forms.BindingNavigator> per salvare i dati dal set di dati nel database (metodo `TableAdapterManager.UpdateAll`).

Il codice di salvataggio generato contiene anche una riga di codice che chiama il metodo `CustomersBindingSource.EndEdit`. In particolare, chiama <xref:System.Windows.Forms.BindingSource.EndEdit%2A> il metodo della prima classe aggiunta al <xref:System.Windows.Forms.BindingSource> form. In altre parole, questo codice viene generato solo per la prima tabella trascinata dalla finestra Origini **dati** nel form. La chiamata al metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> esegue il commit di tutte le modifiche in corso nei controlli associati a dati che si stanno modificando. Pertanto, se un controllo associato a dati ha lo stato attivo e si fa clic sul pulsante **Salva**, prima del salvataggio effettivo verrà eseguito il commit di tutte le modifiche in sospeso nel controllo (metodo `TableAdapterManager.UpdateAll`).

> [!NOTE]
> Il **Progettazione DataSet** aggiunge solo il `BindingSource.EndEdit` codice per la prima tabella rilasciata nel form. Pertanto, è necessario aggiungere una riga di codice per chiamare il metodo `BindingSource.EndEdit` per ogni tabella correlata nel form. Per questa procedura dettagliata, è necessario quindi aggiungere una chiamata al metodo `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Per aggiornare il codice in modo da eseguire il commit delle modifiche apportate alle tabelle correlate prima del salvataggio

1. Fare doppio clic sul pulsante **Salva** in <xref:System.Windows.Forms.BindingNavigator> per aprire **Form1** nell'editor del codice.

2. Aggiungere una riga di codice per chiamare il metodo `OrdersBindingSource.EndEdit` dopo la riga che chiama il metodo `CustomersBindingSource.EndEdit`. Il codice nell'evento Click del pulsante **Salva** deve essere simile al seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs" id="Snippet1":::

Oltre a eseguire il commit delle modifiche apportate a una tabella figlio correlata prima di salvare i dati in un database, potrebbe anche essere necessario eseguire il commit dei record padre appena creati prima di aggiungere i nuovi record figlio in un set di dati. In altre parole, potrebbe essere necessario aggiungere il nuovo record padre ( ) al set di dati prima che i vincoli di chiave esterna consentono l'aggiunta di nuovi record figlio `Customer` ( ) al set di `Orders` dati. A tale scopo, è possibile usare l'evento figlio `BindingSource.AddingNew`.

> [!NOTE]
> Il commit di nuovi record padre dipende dal tipo di controllo usato per l'associazione all'origine dati. In questa procedura dettagliata vengono utilizzati singoli controlli per l'associazione alla tabella padre. Ciò richiede il codice aggiuntivo per eseguire il commit del nuovo record padre. Se i record padre fossero invece visualizzati in un controllo di associazione complesso come , questa chiamata aggiuntiva per il record padre <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource.EndEdit%2A> non sarebbe necessaria. perché la funzionalità di data-binding sottostante del controllo gestisce l'esecuzione del commit dei nuovi record.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Per aggiungere il codice per eseguire il commit dei record padre nel set di dati prima dell'aggiunta dei nuovi record figlio

1. Creare un gestore eventi per l'evento `OrdersBindingSource.AddingNew`.

    - Aprire **Form1** nella visualizzazione Progettazione, **selezionare OrdersBindingSource** nella barra  dei componenti, selezionare **Eventi** nella finestra Proprietà e quindi fare doppio clic sull'evento **AddingNew.**

2. Aggiungere una riga di codice al gestore eventi che chiama il `CustomersBindingSource.EndEdit` metodo . Il codice nel gestore eventi `OrdersBindingSource_AddingNew` deve essere simile al seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs" id="Snippet2":::

## <a name="tableadaptermanager-reference"></a>Informazioni di riferimento su TableAdapterManager

Per impostazione predefinita, `TableAdapterManager` viene generata una classe quando si crea un set di dati contenente tabelle correlate. Per impedire la generazione della classe, modificare il valore della proprietà `Hierarchical Update` del set di dati su false. Quando si trascina una tabella con una relazione nell'area di progettazione di Windows Form o WPF, Visual Studio dichiara una variabile membro della classe. Se non si usa il databinding, è necessario dichiarare manualmente la variabile.

La `TableAdapterManager` classe non è un tipo .NET. Pertanto, non è possibile cercarlo nella documentazione. Viene creato in fase di progettazione come parte del processo di creazione del set di dati.

Di seguito sono riportati i metodi e le proprietà usati di frequente della `TableAdapterManager` classe :

|Membro|Descrizione|
|------------|-----------------|
|Metodo `UpdateAll`|Salva tutti i dati da tutte le tabelle dati.|
|Proprietà`BackUpDataSetBeforeUpdate`|Determina se creare una copia di backup del set di dati prima di eseguire il `TableAdapterManager.UpdateAll` metodo . Boolean.|
|*tableName* `TableAdapter` Proprietà|Rappresenta un oggetto `TableAdapter` . `TableAdapterManager`L'oggetto generato contiene una proprietà per ogni oggetto che `TableAdapter` gestisce. Ad esempio, viene generato un set di dati con una tabella Customers e Orders con un `TableAdapterManager` oggetto che contiene le proprietà e `CustomersTableAdapter` `OrdersTableAdapter` .|
|Proprietà`UpdateOrder`|Controlla l'ordine dei singoli comandi di inserimento, aggiornamento ed eliminazione. Impostare su uno dei valori `TableAdapterManager.UpdateOrderOption` dell'enumerazione .<br /><br /> Per impostazione predefinita, `UpdateOrder` è impostato su **InsertUpdateDelete.** Ciò significa che vengono eseguiti inserimenti, aggiornamenti e quindi eliminazioni per tutte le tabelle nel set di dati.|

## <a name="see-also"></a>Vedi anche

- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
