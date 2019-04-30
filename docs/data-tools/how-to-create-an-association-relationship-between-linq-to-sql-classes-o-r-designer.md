---
title: Come creare una relazione tra classi LINQ to SQL tramite O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b6f0b1f3afec1231778a54c82422d6761995eb1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402787"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procedura: Creare un'associazione tra classi LINQ to SQL (O/R Designer)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando la finestra di dialogo **Editor di associazione**.

Quando si usa la finestra di dialogo **Editor di associazione** per creare un'associazione, è necessario selezionare una classe padre e una classe figlio. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Se, ad esempio, le classi di entità sono state create con mapping al `Northwind Customers` e `Orders` tabelle, il `Customer` classe sarebbe la classe padre e il `Order` classe sarebbe la classe figlio.

> [!NOTE]
> Quando si trascinano tabelle da **Esplora Server** oppure **Esplora Database** nel **Object Relational Designer** (**O/R Designer**), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistente nel database.

## <a name="association-properties"></a>Proprietà dell'associazione
Quando, dopo aver creato un'associazione, la si seleziona in **Object Relational Designer**, nella finestra **Proprietà** è possibile configurare alcune proprietà (l'associazione rappresenta la linea tra le classi correlate). Nella tabella seguente vengono descritte le proprietà di un'associazione.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Cardinality**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|
|**Child Property**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Ad esempio, nell'associazione tra `Customer` e `Order`, se il **Child Property** è impostata su **True**, una proprietà denominata `Orders` viene creato nella classe padre.|
|**Parent Property**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra `Customer` e `Order`, una proprietà denominata `Customer` che fa riferimento al cliente associato per un ordine viene creato nel `Order` classe.|
|**Participating Properties**|Vengono visualizzati le proprietà dell'associazione e un pulsante con i **puntini di sospensione** (...) che consente di riaprire la finestra di dialogo **Editor di associazione**.|
|**Unique**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|

## <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità

1. Fare clic con il pulsante destro del mouse sulla classe di entità che rappresenta la classe padre nell'associazione, scegliere **Aggiungi** e quindi fare clic su **Associazione**.

2. Verificare che nella finestra di dialogo **Editor di associazione** sia selezionata la **Classe padre** corretta.

3. Nella casella combinata selezionare **Classe figlio**.

4. Selezionare le **Proprietà associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Ad esempio, nel `Customers` e `Orders` associazione, il **le proprietà di associazione** sono il `CustomerID` per ogni classe.

5. Fare clic su **OK** per creare l'associazione.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Rappresentare le chiavi primarie](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)