---
title: "Procedura: creare un'associazione (relazione) tra classi di LINQ to SQL (O-R Designer) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610010"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando la finestra di dialogo **Editor di associazione**.

 Quando si usa la finestra di dialogo **Editor di associazione** per creare un'associazione, è necessario selezionare una classe padre e una classe figlio. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Ad esempio, se vengono create classi di entità con mapping alle tabelle Customers e Orders di Northwind, la classe Customer rappresenta la classe padre e la classe Order rappresenta la classe figlio.

> [!NOTE]
> Quando si trascinano le tabelle da **Esplora server** / **Esplora database** [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] a (), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistenti nel database.

 Dopo aver creato un'associazione, quando si seleziona l'associazione in O/R Designer, nella finestra **Proprietà** sono disponibili alcune proprietà configurabili. (L'associazione è la linea tra le classi correlate). Nella tabella seguente vengono fornite le descrizioni per le proprietà di un'associazione.

|Proprietà|Descrizione|
|--------------|-----------------|
|**Cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|
|**Child Property**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Nell'associazione tra Customer e Order, ad esempio, se la **proprietà figlio** è impostata su **true**, nella classe padre viene creata una proprietà denominata Orders.|
|**Parent Property**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra Customer e Order, proprietà denominata Customer che fa riferimento al cliente associato per un ordine creato nella classe Order.|
|**Participating Properties**|Vengono visualizzati le proprietà dell'associazione e un pulsante con i **puntini di sospensione** (...) che consente di riaprire la finestra di dialogo **Editor di associazione**.|
|**Univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|

### <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità

1. Fare clic con il pulsante destro del mouse sulla classe di entità che rappresenta la classe padre nell'associazione, scegliere **Aggiungi** e quindi fare clic su **Associazione**.

2. Verificare che nella finestra di dialogo **Editor di associazione** sia selezionata la **Classe padre** corretta.

3. Nella casella combinata selezionare **Classe figlio**.

4. Selezionare le **Proprietà associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Nell'associazione Customers e Orders, ad esempio, le **proprietà di associazione** sono CustomerID per ogni classe.

5. Fare clic su **OK** per creare l'associazione.

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [metodi DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [procedura: rappresentare le chiavi primarie](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
