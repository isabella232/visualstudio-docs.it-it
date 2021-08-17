---
title: Creare relazioni tra set di dati
description: Creare relazioni tra set di dati in Visual Studio. Informazioni su oggetti e vincoli DataRelation. Creare manualmente una relazione dati in Gestione set di dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 40a964f6b5d21f2e5a601cd81d33fafbdd030189
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052694"
---
# <a name="create-relationships-between-datasets"></a>Creare relazioni tra set di dati
I set di dati che contengono tabelle di dati correlate utilizzano oggetti per rappresentare una relazione padre/figlio tra le tabelle e per restituire record correlati l'uno <xref:System.Data.DataRelation> dall'altro. L'aggiunta di tabelle correlate ai set di dati tramite la Configurazione guidata origine dati o la **Progettazione DataSet**, crea e configura automaticamente <xref:System.Data.DataRelation> l'oggetto .

<xref:System.Data.DataRelation>L'oggetto esegue due funzioni:

- Può rendere disponibili i record correlati a un record in uso. Fornisce record figlio se si è in un record padre ( ) e un record padre se si utilizza <xref:System.Data.DataRow.GetChildRows%2A> un record figlio ( <xref:System.Data.DataRow.GetParentRow%2A> ).

- Può applicare vincoli per l'integrità referenziale, ad esempio l'eliminazione di record figlio correlati quando si elimina un record padre.

È importante comprendere la differenza tra un join reale e la funzione di un <xref:System.Data.DataRelation> oggetto. In un vero join, i record vengono prelevati dalle tabelle padre e figlio e inseriti in un singolo recordset flat. Quando si usa un <xref:System.Data.DataRelation> oggetto , non viene creato alcun nuovo recordset. DataRelation tiene invece traccia della relazione tra le tabelle e mantiene sincronizzati i record padre e figlio.

## <a name="datarelation-objects-and-constraints"></a>Oggetti e vincoli DataRelation
Un <xref:System.Data.DataRelation> oggetto viene usato anche per creare e applicare i vincoli seguenti:

- Vincolo univoco che garantisce che una colonna della tabella non contenga duplicati.

- Vincolo di chiave esterna, che può essere utilizzato per mantenere l'integrità referenziale tra una tabella padre e una tabella figlio in un set di dati.

I vincoli specificati in un oggetto <xref:System.Data.DataRelation> vengono implementati creando automaticamente oggetti appropriati o impostando proprietà. Se si crea un vincolo di chiave esterna usando l'oggetto , le istanze della classe vengono <xref:System.Data.DataRelation> <xref:System.Data.ForeignKeyConstraint> aggiunte alla proprietà <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ChildKeyConstraint%2A> dell'oggetto.

Un vincolo univoco viene implementato semplicemente impostando la proprietà di una colonna di dati su o aggiungendo un'istanza della classe alla proprietà <xref:System.Data.DataColumn.Unique%2A> `true` <xref:System.Data.UniqueConstraint> <xref:System.Data.DataRelation> <xref:System.Data.DataRelation.ParentKeyConstraint%2A> dell'oggetto. Per informazioni sulla sospensione dei vincoli in un set di dati, vedere [Disattivare i vincoli durante il riempimento di un set di dati.](../data-tools/turn-off-constraints-while-filling-a-dataset.md)

### <a name="referential-integrity-rules"></a>Regole di integrità referenziale
Come parte del vincolo di chiave esterna, è possibile specificare regole di integrità referenziale che vengono applicate in tre punti:

- Quando viene aggiornato un record padre

- Quando viene eliminato un record padre

- Quando una modifica viene accettata o rifiutata

Le regole che è possibile creare sono specificate <xref:System.Data.Rule> nell'enumerazione e sono elencate nella tabella seguente.

|Regola del vincolo di chiave esterna|Azione|
| - |------------|
|<xref:System.Data.Rule.Cascade>|La modifica (aggiornamento o eliminazione) apportata al record padre viene apportata anche nei record correlati nella tabella figlio.|
|<xref:System.Data.Rule.SetNull>|I record figlio non vengono eliminati, ma la chiave esterna nei record figlio è impostata su <xref:System.DBNull> . Con questa impostazione, i record figlio possono essere lasciati come "orfani", ovvero non hanno alcuna relazione con i record padre. **Nota:** L'uso di questa regola può comportare dati non validi nella tabella figlio.|
|<xref:System.Data.Rule.SetDefault>|La chiave esterna nei record figlio correlati viene impostata sul relativo valore predefinito (come stabilito dalla proprietà della <xref:System.Data.DataColumn.DefaultValue%2A> colonna).|
|<xref:System.Data.Rule.None>|Non viene apportata alcuna modifica ai record figlio correlati. Con questa impostazione, i record figlio possono contenere riferimenti a record padre non validi.|

Per altre informazioni sugli aggiornamenti nelle tabelle del set di dati, vedere [Salvare di nuovo i dati nel database.](../data-tools/save-data-back-to-the-database.md)

### <a name="constraint-only-relations"></a>Relazioni solo vincoli
Quando si crea un oggetto, è possibile specificare che la relazione deve essere utilizzata solo per applicare vincoli, ovvero non verrà utilizzata anche per accedere ai <xref:System.Data.DataRelation> record correlati. È possibile usare questa opzione per generare un set di dati leggermente più efficiente e che contiene meno metodi rispetto a uno con la funzionalità record correlati. Tuttavia, non sarà possibile accedere ai record correlati. Ad esempio, una relazione solo vincolo impedisce l'eliminazione di un record padre che dispone ancora di record figlio e non è possibile accedere ai record figlio tramite l'elemento padre.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creazione manuale di una relazione dati nel Progettazione DataSet
Quando si creano tabelle dati usando gli strumenti di progettazione dati in Visual Studio, le relazioni vengono create automaticamente se le informazioni possono essere raccolte dall'origine dei dati. Se si aggiungono manualmente tabelle di dati dalla **scheda DataSet** della **casella** degli strumenti , potrebbe essere necessario creare manualmente la relazione. Per informazioni sulla creazione di <xref:System.Data.DataRelation> oggetti a livello di codice, vedere Aggiunta di oggetti [DataRelation.](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations)

Le relazioni tra tabelle di dati vengono visualizzate come righe nel **Progettazione DataSet**, con una chiave e un glifo infinito che rappresentano l'aspetto uno-a-molti della relazione. Per impostazione predefinita, il nome della relazione non viene visualizzato nell'area di progettazione.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Per creare una relazione tra due tabelle di dati

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Trascinare **un oggetto Relation** dalla casella degli strumenti **DataSet** nella tabella dati figlio della relazione.

     Verrà **visualizzata** la finestra di dialogo Relazione che popola la **casella Tabella** figlio con la tabella in cui è stato trascinato l'oggetto **Relation.**

3. Selezionare la tabella padre dalla **casella Tabella** padre . La tabella padre contiene record sul lato "uno" di una relazione uno-a-molti.

4. Verificare che nella casella Tabella figlio sia visualizzata la **tabella figlio** corretta. La tabella figlio contiene record sul lato "molti" di una relazione uno-a-molti.

5. Digitare un nome per la relazione nella **casella Nome** oppure lasciare il nome predefinito in base alle tabelle selezionate. Si tratta del nome dell'oggetto <xref:System.Data.DataRelation> effettivo nel codice.

6. Consente di selezionare le colonne che uniscono le tabelle **negli elenchi Colonne chiave** e Colonne **chiave** esterna .

7. Consente di scegliere se creare una relazione, un vincolo o entrambi.

8. Selezionare o deselezionare la **casella Relazione annidata** . Se si seleziona questa opzione, la proprietà viene impostata su e le righe figlio della relazione vengono annidate all'interno della colonna padre quando tali righe vengono scritte come dati XML o <xref:System.Data.DataRelation.Nested%2A> `true` sincronizzate con <xref:System.Xml.XmlDataDocument> . Per altre informazioni, vedere [Annidamento di datarelation.](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations)

9. Impostare le regole da applicare quando si apportano modifiche ai record in queste tabelle. Per altre informazioni, vedere <xref:System.Data.Rule>.

10. Fare **clic su OK** per creare la relazione. Una linea di relazione viene visualizzata nella finestra di progettazione tra le due tabelle.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Per visualizzare un nome di relazione nel Progettazione DataSet

1. Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un set di dati nel Progettazione DataSet](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Dal menu **Dati** selezionare il comando **Mostra etichette di** relazione per visualizzare il nome della relazione. Deselezionare il comando per nascondere il nome della relazione.

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
