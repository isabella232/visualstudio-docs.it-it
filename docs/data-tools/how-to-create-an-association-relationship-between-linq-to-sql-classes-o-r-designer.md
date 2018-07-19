---
title: Come creare una relazione tra classi LINQ to SQL tramite O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089529"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procedura: creare un'associazione tra classi LINQ to SQL (O/R Designer)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando il **Editor di associazione** nella finestra di dialogo.

È necessario selezionare una classe padre e una classe figlio quando si usa la **Editor di associazione** finestra di dialogo per creare un'associazione. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Se, ad esempio, le classi di entità sono state create con mapping al `Northwind Customers` e `Orders` tabelle, il `Customer` classe sarebbe la classe padre e il `Order` classe sarebbe la classe figlio.

> [!NOTE]
>  Quando si trascinano tabelle da **Esplora Server** oppure **Esplora Database** nel **Object Relational Designer** (**O/R Designer**), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistente nel database.

## <a name="association-properties"></a>Proprietà di associazione
Dopo aver creato un'associazione, quando si seleziona l'associazione nel **O/R Designer**, esistono alcune proprietà configurabili nel **proprietà** finestra. (l'associazione rappresenta la linea tra le classi correlate). Nella tabella seguente vengono descritte le proprietà di un'associazione.

|Proprietà|Descrizione|
|--------------|-----------------|
|**cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|
|**Proprietà figlio**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Ad esempio, nell'associazione tra `Customer` e `Order`, se il **Child Property** è impostata su **True**, una proprietà denominata `Orders` viene creato nella classe padre.|
|**Proprietà padre**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra `Customer` e `Order`, una proprietà denominata `Customer` che fa riferimento al cliente associato per un ordine viene creato nel `Order` classe.|
|**Proprietà partecipanti**|Visualizza le proprietà dell'associazione e fornisce un' **puntini di sospensione** pulsante (...) che si apre nuovamente il **Editor di associazione** nella finestra di dialogo.|
|**univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|

## <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità

1.  Fare doppio clic la classe di entità che rappresenta la classe padre nell'associazione, scegliere **Add**, quindi fare clic su **Association**.

2.  Verificare che i valori corretti **classe padre** sia selezionato nel **Editor di associazione** nella finestra di dialogo.

3.  Selezionare il **classe figlio** nella casella combinata.

4.  Selezionare il **le proprietà di associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Ad esempio, nel `Customers` e `Orders` associazione, il **le proprietà di associazione** sono il `CustomerID` per ogni classe.

5.  Fare clic su **OK** per creare l'associazione.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: rappresentare le chiavi primarie](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)