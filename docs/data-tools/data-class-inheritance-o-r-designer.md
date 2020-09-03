---
title: Ereditarietà delle classi di dati (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462395"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà delle classi di dati (Object Relational Designer)

Analogamente ad altri oggetti, le classi LINQ to SQL possono usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. Il **Object Relational Designer** (**O/R Designer**) supporta il concetto di ereditarietà a tabella singola poiché viene spesso implementato nei sistemi relazionali.

Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Si consideri, ad esempio, una `Persons` tabella che contiene tutti i dipendenti di una società. alcune delle quali sono dipendenti mentre altre sono manager. La `Persons` tabella contiene una colonna denominata `Type` con un valore pari a 1 per i Manager e un valore pari a 2 per i dipendenti. La `Type` colonna è la colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolare la classe con solo i record con `Type` valore 2.

Quando si configura l'ereditarietà nelle classi dell'entità usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], trascinare due volte la singola tabella che contiene i dati di ereditarietà sulla finestra di progettazione: una volta per ogni classe nella gerarchia di ereditarietà. Dopo avere aggiunto le tabelle alla finestra di progettazione, connetterle con un elemento di ereditarietà dalla casella degli strumenti **Object Relational Designer** e quindi impostare le quattro proprietà nella finestra **Proprietà**.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà

Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|Proprietà|Descrizione|
|--------------|-----------------|
|**Proprietà Discriminator**|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|**Valore discriminante classe base**|Valore (nella colonna designata come **proprietà Discriminator**) che determina che un record è della classe di base.|
|**Valore discriminante classe derivata**|Valore (nella proprietà designata come **proprietà Discriminator**) che determina che un record è della classe derivata.|
|**Valore predefinito di ereditarietà**|Classe popolata quando il valore della proprietà designato come **Proprietà discriminatore** non corrisponde al **valore del discriminatore della classe base** o al **valore del discriminatore della classe derivata**.|

La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con **Progettazione relazionale**elementi.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Configurare l'ereditarietà usando O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà a tabella singola usando la **finestra di progettazione di O/R**.|
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate su come configurare le classi di entità che usano l'ereditarietà a tabella singola usando la finestra di **progettazione di O/R**.|

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introduzione](/dotnet/framework/data/adonet/sql/linq/getting-started)