---
title: Relazioni nei DataSet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e78b4efa9c56a46ea182d3ff3b77a7452d0c547f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954760"
---
# <a name="relationships-in-datasets"></a>Relazioni nei DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
I set di dati che contengono i dati correlati tabelle utilizzano <xref:System.Data.DataRelation> oggetti per rappresentare una relazione padre/figlio tra le tabelle e per restituire i record correlati tra loro. Aggiunta di tabelle correlate ai set di dati con il **configurazione guidata origine dati**, o il **Progettazione Dataset**, crea e configura il <xref:System.Data.DataRelation> oggetto per l'utente.  
  
 Il <xref:System.Data.DataRelation> oggetto esegue due funzioni:  
  
- Può rendere disponibili i record correlati a un record che si sta lavorando. Fornisce i record figlio in presenza di un record padre (<xref:System.Data.DataRow.GetChildRows%2A>) e un record padre se si lavora con un record figlio (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
- È possibile applicare vincoli per l'integrità referenziale, ad esempio l'eliminazione di record figlio correlati quando si elimina un record padre.  
  
  È importante comprendere la differenza tra un join e la funzione di un <xref:System.Data.DataRelation> oggetto. In un join, i record vengono ricavati dalle tabelle padre e figlio e inserire in un unico set di record. Quando si usa un <xref:System.Data.DataRelation> dell'oggetto, non viene creato alcun nuovo set di record. Al contrario, la DataRelation rileva la relazione tra tabelle e mantiene sincronizzata record padre e figlio.  
  
## <a name="datarelation-objects-and-constraints"></a>I vincoli e oggetti DataRelation  
 Oggetto <xref:System.Data.DataRelation> oggetto viene usato anche per creare e imporre i vincoli seguenti:  
  
- Un vincolo univoco, che garantisce che una colonna nella tabella non contiene duplicati.  
  
- Un vincolo foreign key, che può essere usato per mantenere l'integrità referenziale tra una tabella padre e figlio in un set di dati.  
  
  I vincoli specificati in un <xref:System.Data.DataRelation> oggetto vengono implementate automaticamente la creazione di oggetti appropriati o impostando proprietà. Se si crea un vincolo foreign key tramite il <xref:System.Data.DataRelation> (oggetto), le istanze del <xref:System.Data.ForeignKeyConstraint> classe vengono aggiunti per il <xref:System.Data.DataRelation> dell'oggetto <xref:System.Data.DataRelation.ChildKeyConstraint%2A> proprietà.  
  
  Viene implementato un vincolo unique impostando semplicemente il <xref:System.Data.DataColumn.Unique%2A> proprietà di una colonna di dati da `true` o tramite l'aggiunta di un'istanza del <xref:System.Data.UniqueConstraint> classe per il <xref:System.Data.DataRelation> dell'oggetto <xref:System.Data.DataRelation.ParentKeyConstraint%2A> proprietà. Per informazioni sulla sospensione dei vincoli in un set di dati, vedere [disattivare i vincoli durante il riempimento di un set di dati](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Regole di integrità referenziale  
 Come parte del vincolo di chiave esterna, è possibile specificare regole di integrità referenziale in tre punti:  
  
- Quando viene aggiornato un record padre  
  
- Quando viene eliminato un record padre  
  
- Quando una modifica è accettata o rifiutata  
  
  Le regole che è possibile apportare siano specificate nel <xref:System.Data.Rule> enumerazione ed elencate nella tabella seguente.  
  
|Regola del vincolo di chiave esterna|Operazione|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|È anche apportare la modifica (aggiornamento o eliminazione) apportata al record padre nei record correlati nella tabella figlio.|  
|<xref:System.Data.Rule>|I record figlio non vengono eliminati, ma la chiave esterna nel record figlio è impostata su <xref:System.DBNull>. Con questa impostazione, i record figlio possono essere lasciati come "orfani", vale a dire, non dispongono di alcuna relazione con i record padre. **Nota:**  Con questa regola può comportare dati non validi nella tabella figlio.|  
|<xref:System.Data.Rule>|La chiave esterna nei record figlio correlati è impostata sul valore predefinito (come stabilito in base alla colonna <xref:System.Data.DataColumn.DefaultValue%2A> proprietà).|  
|<xref:System.Data.Rule>|Viene apportata alcuna modifica ai record figlio correlati. Con questa impostazione, i record figlio possono contenere riferimenti ai record padre non valido.|  
  
 Per altre informazioni sugli aggiornamenti nelle tabelle di set di dati, vedere [salvare i dati nel database](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Relazioni di solo vincolo  
 Quando si crea un <xref:System.Data.DataRelation> dell'oggetto, è possibile scegliere di specificare che la relazione venga utilizzata solo per imporre vincoli, vale a dire, non verrà anche essere utilizzato per accedere ai record correlati. È possibile usare questa opzione per generare un set di dati che è leggermente più efficiente e che contiene i metodi di un numero minore rispetto a uno con la funzionalità di record correlati. Tuttavia, non sarà in grado di accedere ai record correlati. Ad esempio, una solo vincolo di relazione si impedisce l'eliminazione di un record padre che presenta ancora record figlio e i record figlio non è possibile accedere tramite l'elemento padre.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Creazione manuale di una relazione dati in Progettazione Dataset  
 Quando si creano le tabelle di dati usando gli strumenti di progettazione dei dati in Visual Studio, le relazioni vengono create automaticamente se le informazioni possono essere raccolte dall'origine dei dati. Se si aggiungono manualmente le tabelle di dati dal **set di dati** scheda della finestra di **della casella degli strumenti**, potrebbe essere necessario creare manualmente la relazione. Per informazioni sulla creazione <xref:System.Data.DataRelation> degli oggetti a livello di codice, vedere [aggiunta di oggetti DataRelation](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Le relazioni tra tabelle di dati vengono visualizzati come righe nel **Progettazione Dataset**, con una chiave e un numero infinito un'icona che rappresenta l'aspetto di uno-a-molti della relazione. Per impostazione predefinita, il nome del relationshipCommentEnd Id = '1c8c78e19b7fa441' non viene visualizzata nell'area di progettazione.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>Per creare una relazione tra due tabelle dati  
  
1.  Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura: Aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Trascinare un **relazione** dell'oggetto dalle **set di dati** casella degli strumenti nella tabella dati figlio nella relazione.  
  
     Il **relazione** verrà visualizzata la finestra di dialogo, popolamento il **tabella figlio** casella con la tabella che è stato trascinato il **relazione** dell'oggetto in.  
  
3.  Selezionare la tabella padre di **tabella padre** casella. La tabella padre contiene record sul lato "uno" di una relazione uno-a-molti.  
  
4.  Verificare che la tabella figlio corretto sia visualizzata nei **tabella figlio** casella. La tabella figlio contiene i record sul lato "molti" di una relazione uno-a-molti.  
  
5.  Digitare un nome per la relazione nel **nome** casella o lasciare il nome predefinito basato sulle tabelle selezionate. Si tratta del nome dell'effettivo <xref:System.Data.DataRelation> oggetto nel codice.  
  
6.  Selezionare le colonne che uniscono in join le tabelle nel **colonne chiave** e **colonne di chiavi esterne** Elenca.  
  
7.  Scegliere se creare una relazione, vincolo o entrambi. Per informazioni, vedere [Introduzione agli oggetti DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8.  Selezionare o deselezionare i **relazione annidata** casella. Selezionando questa opzione imposta la <xref:System.Data.DataRelation.Nested%2A> proprietà `true`, e il figlio della relazione annidata all'interno della colonna padre quando le righe vengono scritte come dati XML o sincronizzate con righe <xref:System.Xml.XmlDataDocument>. Per altre informazioni, vedere [annidamento di oggetti DataRelation](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Impostare le regole da applicare quando si apportano modifiche ai record in queste tabelle. Per altre informazioni, vedere <xref:System.Data.Rule>.  
  
10. Fare clic su **OK** per creare la relazione. Verrà visualizzata una linea di relazione nella finestra di progettazione tra le due tabelle.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Per visualizzare un nome della relazione nella finestra di progettazione set di dati  
  
1.  Aprire il set di dati in **Progettazione DataSet**. Per altre informazioni, vedere [Procedura: Aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Dal **dati** menu, seleziona la **Mostra etichette di relazione** comando per visualizzare il nome della relazione. Deselezionare tale comando per nascondere il nome della relazione.
