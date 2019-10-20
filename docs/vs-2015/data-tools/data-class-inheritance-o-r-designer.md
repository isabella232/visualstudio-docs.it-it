---
title: Ereditarietà delle classi di dati (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e7dfc2b1137b30a03425f663d70e12c528dad39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657404"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà delle classi di dati (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali.

 Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società, alcune delle quali sono dipendenti mentre altre sono manager. La tabella Persons contiene una colonna denominata Type, che presenta un valore 1 per i manager e un valore 2 per i dipendenti, e che costituisce la colonna discriminante. In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un valore 2 nella colonna Type.

 Quando si configura l'ereditarietà nelle classi dell'entità usando [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], trascinare due volte la singola tabella che contiene i dati di ereditarietà sulla finestra di progettazione: una volta per ogni classe nella gerarchia di ereditarietà. Dopo avere aggiunto le tabelle alla finestra di progettazione, connetterle con un elemento di ereditarietà dalla casella degli strumenti **Object Relational Designer** e quindi impostare le quattro proprietà nella finestra **Proprietà**.

## <a name="inheritance-properties"></a>Proprietà di ereditarietà
 Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:

|proprietà|Descrizione|
|--------------|-----------------|
|Proprietà Discriminator|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|
|Valore discriminante classe base|Valore (nella colonna definita come proprietà Discriminator) che determina che un record fa parte della classe base.|
|Valore discriminante classe derivata|Valore (nella proprietà definita come proprietà Discriminator) che determina che un record fa parte della classe derivata.|
|Valore predefinito di ereditarietà|Classe che deve essere popolata quando il valore della proprietà designato come **proprietà Discriminator** non corrisponde al **valore del discriminatore della classe base** o al **valore del discriminatore della classe derivata**.|

 La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Configurare l'ereditarietà usando O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà mediante [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità che usano l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|

## <a name="see-also"></a>Vedere anche
 Procedura dettagliata per la [creazione di classi di LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [: creazione di classi di LINQ to SQL usando l'ereditarietà a tabella singola (o/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [Introduzione](https://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)
