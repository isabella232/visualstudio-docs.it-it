---
title: Ereditarietà delle classi di dati (Object Relational Designer)
description: Usare l'ereditarietà delle classi di dati in Object Relational Designer (O/R Designer), uno strumento LINQ to SQL classe in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 82c1c07ec9fb7e19a2d4e126358d124d88c79ff1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154914"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà delle classi di dati (Object Relational Designer)

Analogamente ad altri oggetti, LINQ to SQL classi possono usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. La **Object Relational Designer** (**Progettazione relazionale** oggetti ) supporta il concetto di ereditarietà a tabella singola, perché viene spesso implementata nei sistemi relazionali.

Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Si consideri ad esempio `Persons` una tabella che contiene tutti gli dipendenti di una società. alcune delle quali sono dipendenti mentre altre sono manager. La tabella contiene una colonna denominata con valore 1 per i responsabili e `Persons` `Type` un valore 2 per i dipendenti. La `Type` colonna è la colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolare la classe con solo i record con `Type` valore 2.

Quando si configura l'ereditarietà nelle classi dell'entità usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare due volte la singola tabella che contiene i dati di ereditarietà sulla finestra di progettazione: una volta per ogni classe nella gerarchia di ereditarietà. Dopo avere aggiunto le tabelle alla finestra di progettazione, connetterle con un elemento di ereditarietà dalla casella degli strumenti **Object Relational Designer** e quindi impostare le quattro proprietà nella finestra **Proprietà**.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà

Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|Proprietà|Descrizione|
|--------------|-----------------|
|**Proprietà Discriminator**|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|**Valore discriminante classe base**|Valore (nella colonna designata come proprietà **discriminatore)** che determina che un record è della classe di base.|
|**Valore discriminante classe derivata**|Valore (nella proprietà designata come proprietà **discriminatore)** che determina che un record è della classe derivata.|
|**Valore predefinito di ereditarietà**|Classe popolata quando il valore nella proprietà designata come Proprietà **discriminatore** non corrisponde al valore discriminatore della classe **base** o al valore del **discriminatore** della classe derivata .|

La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con **O/R Designer.**

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Configurare l'ereditarietà usando O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare classi di entità che usano l'ereditarietà a tabella singola tramite **O/R Designer.**|
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fornisce istruzioni dettagliate su come configurare le classi di entità che usano l'ereditarietà a tabella singola tramite **O/R Designer.**|

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introduzione](/dotnet/framework/data/adonet/sql/linq/getting-started)
