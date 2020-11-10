---
title: Relazioni tra LINQ to SQL classi
description: Creare un'associazione tra LINQ to SQL classi di entità utilizzando la finestra di dialogo Editor dell'associazione in Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 96932dca3d7f8799c316e05dc36c3f38a0e8110f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436320"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Procedura: creare un'associazione tra classi di LINQ to SQL (O/R Designer)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando la finestra di dialogo **Editor di associazione**.

Quando si usa la finestra di dialogo **Editor di associazione** per creare un'associazione, è necessario selezionare una classe padre e una classe figlio. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Se, ad esempio, sono state create classi di entità con mapping alle `Northwind Customers` `Orders` tabelle e, la classe `Customer` sarà la classe padre e la classe `Order` sarà la classe figlio.

> [!NOTE]
> Quando si trascinano le tabelle da **Esplora server** o **Esplora database** nel **Object Relational Designer** ( **o/R Designer** ), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistenti nel database.

## <a name="association-properties"></a>Proprietà dell'associazione
Quando, dopo aver creato un'associazione, la si seleziona in **Object Relational Designer** , nella finestra **Proprietà** è possibile configurare alcune proprietà (L'associazione è la linea tra le classi correlate). Nella tabella seguente vengono fornite le descrizioni per le proprietà di un'associazione.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|
|**Child Property**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Nell'associazione tra e, ad esempio `Customer` , `Order` se la **proprietà figlio** è impostata su **true** , viene creata una proprietà denominata nella `Orders` classe padre.|
|**Parent Property**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Nell'associazione tra e, ad esempio `Customer` , `Order` una proprietà denominata `Customer` che fa riferimento al cliente associato per un ordine viene creata sulla `Order` classe.|
|**Participating Properties**|Vengono visualizzati le proprietà dell'associazione e un pulsante con i **puntini di sospensione** (...) che consente di riaprire la finestra di dialogo **Editor di associazione**.|
|**Univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|

## <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità

1. Fare clic con il pulsante destro del mouse sulla classe di entità che rappresenta la classe padre nell'associazione, scegliere **Aggiungi** e quindi fare clic su **Associazione**.

2. Verificare che nella finestra di dialogo **Editor di associazione** sia selezionata la **Classe padre** corretta.

3. Nella casella combinata selezionare **Classe figlio**.

4. Selezionare le **Proprietà associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Nell' `Customers` associazione e, ad esempio `Orders` , le **proprietà di associazione** sono `CustomerID` per ogni classe.

5. Fare clic su **OK** per creare l'associazione.

## <a name="see-also"></a>Vedere anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: creazione di classi di LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: rappresentare le chiavi primarie](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
