---
title: Proprietà di operazioni in diagrammi classi UML | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671342"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Proprietà di operazioni in diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma classi UML è possibile aggiungere *operazioni* a classi e interfacce. Un'operazione è una funzione o un metodo che può essere eseguito da un'istanza di una classe o di un'interfaccia.

 Per aggiungere un'operazione, fare clic con il pulsante destro del mouse sulla classe o sull'interfaccia, scegliere **Aggiungi**, quindi fare clic su **operazione**.

 Se le operazioni di una classe nel diagramma non sono visibili, fare clic sulla freccia di espansione nella parte superiore della classe o dell'interfaccia. Se è possibile visualizzare l'intestazione dell' **operazione** , fare clic su **[+]** per espandere la sezione operazioni.

## <a name="signature-of-an-operation"></a>Firma di un'operazione
 La firma di un'operazione è la riga di testo che la rappresenta in una classe o in un'interfaccia di un diagramma classi UML. e ha il formato seguente:

 \+ OperationName (parametro1: tipo1 [*],...): ReturnType [ \* ]

 \+ indica la visibilità pubblica. Gli altri valori consentiti sono: (private), # (protected), ~ (package).

 `OperationName` viene sottolineato se la proprietà **is static** è true ed è in corsivo se la proprietà **is abstract** è true.

 `: ReturnType` viene omesso se non è definito alcun tipo restituito.

 `[*]` indica la molteplicità di un parametro o di un tipo restituito. Viene omesso se la molteplicità è 1.

 Per una descrizione completa di queste proprietà, vedere la sezione successiva.

## <a name="properties"></a>Proprietà
 In questa sezione sono illustrate le proprietà di un'operazione in una classe o in un'interfaccia di un diagramma classi UML.

 Per visualizzare le proprietà di un'operazione, fare clic con il pulsante destro del mouse sull'operazione nella classe o nell'interfaccia del diagramma e quindi scegliere **Proprietà**. Le proprietà vengono visualizzate nella finestra **Proprietà** .

|      Proprietà       |   Predefinito    |                                                                                                                                                                                 Descrizione                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Name**       | (nuovo nome) |                                                                                                                                                                Deve essere univoco all'interno del tipo che lo contiene.                                                                                                                                                                 |
|   **Parametri**    |    (nessuna)    |      Elenco con il formato <em>nome</em>**:**<em>tipo</em>**,** <em>nome</em>**:**<em>tipo</em>**,.** ... Per modificare l'elenco, fare clic su **[...]** .<br /><br /> I tipi possono essere primitivi o definiti nel modello. Se si immette un nome per un nuovo tipo di questa proprietà, verrà aggiunto un tipo nella sezione **Tipi non specificati** di Esplora modelli UML.      |
|   **Tipo restituito**   |    (nessuna)    |                                                                               **(nessuno)**, o un tipo primitivo o un tipo definito nel modello. Se si immette un nome per un nuovo tipo di questa proprietà, verrà aggiunto un tipo nella sezione **Tipi non specificati** di Esplora modelli UML.                                                                                |
| **Postconditions**  |    (nessuna)    |                                                                                                                         Condizione facoltativa che specifica una relazione tra lo stato del sistema prima e dopo l'esecuzione dell'operazione.                                                                                                                         |
|  **Preconditions**  |    (nessuna)    |                                                                                                                            Condizione facoltativa che specifica i presupposti sullo stato del sistema prima dell'inizio dell'esecuzione dell'operazione.                                                                                                                            |
| **Body Conditions** |    (nessuna)    |                                                                                                                                                       Vincolo facoltativo sui valori restituiti dall'operazione.                                                                                                                                                       |
|   **Visibilità**    |    Pubblico    |                  I valori consentiti e i caratteri visualizzati nella firma sono:<br /><br /> **+ Public** : visibile a livello globale<br /><br /> **- Private** : non visibile all'esterno del tipo proprietario<br /><br /> **# Protected** : visibile ai tipi derivati dal proprietario<br /><br /> **~ Package** : visibile agli altri tipi all'interno dello stesso pacchetto.                   |
|    **Firma**    |  +*Nome*()   |                                                                                      Riepiloga la visibilità, il nome, i parametri e il tipo restituito di questa operazione. È possibile modificare tali proprietà modificando la firma sul diagramma o modificando le singole proprietà.                                                                                      |
|   **Elementi di lavoro**    | 0 elementi associati |                                                                                                  Numero di elementi di lavoro associati. Sola lettura.<br /><br /> Per altre informazioni, vedere [collegare elementi del modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Concorrenza**   |  Sequenziale  | **Sequenziale** : l'operazione è o verrà progettata senza controllo della concorrenza. L'esecuzione contemporanea di più chiamate a questa operazione potrebbe causare errori.<br /><br /> **Sorvegliato** : l'operazione verrà bloccata automaticamente fino al completamento di altre istanze di.<br /><br /> **Simultaneo** : l'operazione è progettata in modo da consentire l'esecuzione simultanea di più chiamate a essa. |
|    **Is Static**    |    Falso     |                                                                                                  Se true, questa operazione viene condivisa tra tutte le istanze di questo tipo.<br /><br /> Se true, il nome dell'operazione sarà sottolineato laddove viene visualizzato nel diagramma.                                                                                                   |
|   **Astratto**   |    Falso     |                                                                                                                                        Se true, a questa operazione non è associato alcun codice. La classe proprietaria è quindi astratta.                                                                                                                                         |
|     **Is Leaf**     |    Falso     |                                                                                                                                              La finestra di progettazione indica che non è possibile eseguire l'override di questa operazione nelle classi derivate.                                                                                                                                              |
|    **Is Query**     |    Falso     |                                                                                                 Se true, non vengono apportate modifiche significative allo stato del sistema da questa operazione. Può quindi essere usata ad esempio in un test per controllare lo stato del sistema.                                                                                                  |
|  **Molteplicità**   |      1       |                                 **1** : valore singolo del tipo specificato.<br /><br /> **0.. 1** : può essere `null` .<br /><br /> \* : raccolta di valori del tipo specificato.<br /><br /> **1.. \\ .** \* raccolta contenente almeno un valore.<br /><br /> *n* `..` *m* : raccolta che contiene valori compresi tra `n` e `m` .                                  |
|   **Is Ordered**    |    Falso     |                                                                                                                                             Se true, la raccolta forma un elenco sequenziale. Per la **molteplicità** maggiore di 1.                                                                                                                                              |
|    **Univoco**    |    Falso     |                                                                                                                                         Se true, non sono presenti valori duplicati nella raccolta. Per la **molteplicità** maggiore di 1.                                                                                                                                         |

## <a name="see-also"></a>Vedere anche
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md) [proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [proprietà di associazioni nei diagrammi](../modeling/properties-of-associations-on-uml-class-diagrams.md) classi UML diagrammi classi [UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)
