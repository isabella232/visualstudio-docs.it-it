---
title: Proprietà di operazioni su UML diagrammi classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9d53c44a70818739e02c34071fd81b8bdfdec87f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968492"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Proprietà di operazioni in diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma classi UML, è possibile aggiungere *operazioni* a classi e interfacce. Un'operazione è una funzione o un metodo che può essere eseguito da un'istanza di una classe o di un'interfaccia.  

 Per aggiungere un'operazione, fare doppio clic la classe o interfaccia, scegliere **Add**, quindi fare clic su **operazione**.  

 Se le operazioni di una classe nel diagramma non sono visibili, fare clic sulla freccia di espansione nella parte superiore della classe o dell'interfaccia. Se è possibile vedere le **operazione** intestazione, fare clic su **[+]** per espandere la sezione relativa alle operazioni.  

## <a name="signature-of-an-operation"></a>Firma di un'operazione  
 La firma di un'operazione è la riga di testo che la rappresenta in una classe o in un'interfaccia di un diagramma classi UML. Ha il formato seguente:  

 \+ OperationName (parameter1: Type1 [*]...) : ReturnType [\*]  

 \+ indica la visibilità pubblica. Gli altri valori consentiti sono: (private), # (protected), ~ (package).  

 `OperationName` è sottolineato se la **Is Static** proprietà è true, mentre è in corsivo se la **Is Abstract** proprietà è true.  

 `: ReturnType` viene omesso se non è definito alcun tipo restituito.  

 `[*]` indica la molteplicità di un parametro o di un tipo restituito. Viene omesso se la molteplicità è 1.  

 Per una descrizione completa di queste proprietà, vedere la sezione successiva.  

## <a name="properties"></a>Proprietà  
 In questa sezione sono illustrate le proprietà di un'operazione in una classe o in un'interfaccia di un diagramma classi UML.  

 Per visualizzare le proprietà di un'operazione, fare doppio clic sull'operazione nella classe o interfaccia nel diagramma e quindi fare clic su **proprietà**. Le proprietà vengono visualizzate nel **proprietà** finestra.  


|      Proprietà       |   Impostazione predefinita    |                                                                                                                                                                                 Descrizione                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Name**       | (nuovo nome) |                                                                                                                                                                Deve essere univoco all'interno del tipo che lo contiene.                                                                                                                                                                 |
|   **Parametri**    |    (nessuno)    |      Un elenco che ha il formato <em>name</em>**:**<em>tipo</em>**,** <em>nome</em>**:**  <em>Tipo di</em>**,...** Fare clic su **[...]**  per modificare l'elenco.<br /><br /> I tipi possono essere primitivi o definiti nel modello. Se si immette un nome per un nuovo tipo di questa proprietà, verrà aggiunto un tipo nella sezione **Tipi non specificati** di Esplora modelli UML.      |
|   **Tipo restituito**   |    (nessuno)    |                                                                               **(nessuno)** , o un tipo primitivo o un tipo definito nel modello. Se si immette un nome per un nuovo tipo di questa proprietà, verrà aggiunto un tipo nella sezione **Tipi non specificati** di Esplora modelli UML.                                                                                |
| **Postcondizioni**  |    (nessuno)    |                                                                                                                         Condizione facoltativa che specifica una relazione tra lo stato del sistema prima e dopo l'esecuzione dell'operazione.                                                                                                                         |
|  **Precondizioni**  |    (nessuno)    |                                                                                                                            Condizione facoltativa che specifica i presupposti sullo stato del sistema prima dell'inizio dell'esecuzione dell'operazione.                                                                                                                            |
| **Condizioni del corpo** |    (nessuno)    |                                                                                                                                                       Vincolo facoltativo sui valori restituiti dall'operazione.                                                                                                                                                       |
|   **Visibilità**    |    Public    |                  I valori consentiti e i caratteri visualizzati nella firma sono:<br /><br /> **+ Public** : visibile a livello globale<br /><br /> **- Private** : non visibile all'esterno del tipo proprietario<br /><br /> **# Protected** : visibile ai tipi derivati dal proprietario<br /><br /> **~ Package** : visibile agli altri tipi all'interno dello stesso pacchetto.                   |
|    **Firma**    |  +*Name*()   |                                                                                      Riepiloga la visibilità, il nome, i parametri e il tipo restituito di questa operazione. È possibile modificare tali proprietà modificando la firma sul diagramma o modificando le singole proprietà.                                                                                      |
|   **Elementi di lavoro**    | 0 elementi associati |                                                                                                  Numero di elementi di lavoro associati. Sola lettura.<br /><br /> Per altre informazioni, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Concorrenza**   |  Sequential  | **Sequenziale** -l'operazione viene o verrà progettato senza il controllo della concorrenza. L'esecuzione contemporanea di più chiamate a questa operazione potrebbe causare errori.<br /><br /> **Sorvegliato** -l'operazione verrà bloccata automaticamente fino al completamento di altre istanze di esso.<br /><br /> **Simultanee** -l'operazione è progettata in modo che più chiamate a esso possono essere eseguite contemporaneamente. |
|    **È statico**    |    False     |                                                                                                  Se true, questa operazione viene condivisa tra tutte le istanze di questo tipo.<br /><br /> Se true, il nome dell'operazione sarà sottolineato laddove viene visualizzato nel diagramma.                                                                                                   |
|   **È di tipo Abstract**   |    False     |                                                                                                                                        Se true, a questa operazione non è associato alcun codice. La classe proprietaria è quindi astratta.                                                                                                                                         |
|     **È nodo foglia**     |    False     |                                                                                                                                              La finestra di progettazione indica che non è possibile eseguire l'override di questa operazione nelle classi derivate.                                                                                                                                              |
|    **Query**     |    False     |                                                                                                 Se true, non vengono apportate modifiche significative allo stato del sistema da questa operazione. Può quindi essere usata ad esempio in un test per controllare lo stato del sistema.                                                                                                  |
|  **Molteplicità**   |      1       |                                 **1** -un singolo valore del tipo specificato.<br /><br /> **0..1** -può essere `null`.<br /><br /> \* -una raccolta di valori del tipo specificato.<br /><br /> **1..\\**  \* : una raccolta che contiene almeno un valore.<br /><br /> *n* `..` *m* -una raccolta che contenga tra `n` e `m` valori.                                  |
|   **È ordinato**    |    False     |                                                                                                                                             Se true, la raccolta forma un elenco sequenziale. Per la **molteplicità** più di 1.                                                                                                                                              |
|    **È univoco**    |    False     |                                                                                                                                         Se true, non sono presenti valori duplicati nella raccolta. Per la **molteplicità** più di 1.                                                                                                                                         |

## <a name="see-also"></a>Vedere anche  
 [Diagrammi delle classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)
