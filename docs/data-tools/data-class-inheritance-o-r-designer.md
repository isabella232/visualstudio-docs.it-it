---
title: Ereditarietà della classe di dati (O-R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756737"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà della classe di dati (O/R Designer)

Analogamente ad altri oggetti, classi LINQ to SQL può usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. Il **Object Relational Designer** (**O/R Designer**) supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali.

Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Si consideri, ad esempio, un `Persons` tabella che contiene tutte le persone impiegate in una società. alcune delle quali sono dipendenti mentre altre sono manager. Il `Persons` tabella contiene una colonna denominata `Type` che presenta un valore pari a 1 per i responsabili e il valore 2 per i dipendenti. Il `Type` colonna è la colonna discriminatore. In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un `Type` valore 2.

Quando si configura l'ereditarietà nelle classi di entità utilizzando la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare la singola tabella che contiene i dati di ereditarietà nella finestra di progettazione due volte: una volta per ogni classe nella gerarchia di ereditarietà. Dopo aver aggiunto le tabelle nella finestra di progettazione, connetterle con un elemento di ereditarietà dal **Object Relational Designer** casella degli strumenti e quindi impostare le quattro proprietà di ereditarietà nel **proprietà** finestra.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà

Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|Proprietà|Descrizione|
|--------------|-----------------|
|**Proprietà Discriminator**|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|**Valore discriminante classe base**|Il valore (nella colonna definita come il **Discriminator Property**) che determina che un record fa parte della classe di base.|
|**Valore discriminante classe derivata**|Il valore (nella proprietà definita come il **Discriminator Property**) che determina che un record fa parte della classe derivata.|
|**Valore predefinito di ereditarietà**|La classe che viene popolata quando il valore nella proprietà definita come il **proprietà Discriminator** corrisponde a uno il **Base Class Discriminator Value** o **classe derivata da Valore discriminante**.|

La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Gli argomenti seguenti forniscono una spiegazione più chiara di come configurare l'ereditarietà con il **O/R Designer**.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà a tabella singola tramite il **O/R Designer**.|
|[Procedura dettagliata: Creazione di LINQ alle classi di SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate su come configurare le classi di entità che usano l'ereditarietà a tabella singola tramite il **O/R Designer**.|

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introduzione](/dotnet/framework/data/adonet/sql/linq/getting-started)