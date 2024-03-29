---
title: Relazioni tra LINQ to SQL classi
description: Creare un'associazione LINQ to SQL classi di entità usando la finestra di dialogo Editor associazioni in Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e7f686e86f0bb4743e8cbb45e29d0ebcb2b22e5e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631319"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procedura: Creare un'associazione tra LINQ to SQL classi (O/R Designer)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando la finestra di dialogo **Editor di associazione**.

Quando si usa la finestra di dialogo **Editor di associazione** per creare un'associazione, è necessario selezionare una classe padre e una classe figlio. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Ad esempio, se sono state create classi di entità mappate alle tabelle e , la classe sarà la classe padre e la classe `Northwind Customers` `Orders` sarà la classe `Customer` `Order` figlio.

> [!NOTE]
> Quando si trascinano tabelle da **Esplora server** o **Esplora database** nel **Object Relational Designer** **(** Progettazione relazionale oggetti ), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistenti nel database.

## <a name="association-properties"></a>Proprietà dell'associazione
Quando, dopo aver creato un'associazione, la si seleziona in **Object Relational Designer**, nella finestra **Proprietà** è possibile configurare alcune proprietà L'associazione è la linea tra le classi correlate. Nella tabella seguente vengono fornite le descrizioni delle proprietà di un'associazione.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|
|**Child Property**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Ad esempio, nell'associazione tra e , se la proprietà figlio è impostata su True , viene creata una proprietà `Customer` `Order` denominata nella classe   `Orders` padre.|
|**Proprietà padre**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra e , nella classe viene creata una proprietà denominata che fa riferimento al cliente `Customer` `Order` associato per un `Customer` `Order` ordine.|
|**Participating Properties**|Vengono visualizzati le proprietà dell'associazione e un pulsante con i **puntini di sospensione** (...) che consente di riaprire la finestra di dialogo **Editor di associazione**.|
|**Univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|

## <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità

1. Fare clic con il pulsante destro del mouse sulla classe di entità che rappresenta la classe padre nell'associazione, scegliere **Aggiungi** e quindi fare clic su **Associazione**.

2. Verificare che nella finestra di dialogo **Editor di associazione** sia selezionata la **Classe padre** corretta.

3. Nella casella combinata selezionare **Classe figlio**.

4. Selezionare le **Proprietà associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Ad esempio, `Customers` nell'associazione `Orders` e le proprietà **dell'associazione** sono `CustomerID` per ogni classe.

5. Fare clic su **OK** per creare l'associazione.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione LINQ to SQL classi](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Rappresentare chiavi primarie](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
