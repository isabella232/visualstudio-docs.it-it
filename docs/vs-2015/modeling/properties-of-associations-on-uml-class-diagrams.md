---
title: Proprietà delle associazioni nei UML diagrammi classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c029a29b2d81f7a6ca64f47aab15caf5119d172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154871"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Proprietà delle associazioni nei diagrammi classi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma classi UML, è possibile tracciare *associazioni* tra qualsiasi coppia di tipi. Un tipo è una classe, un'interfaccia o un'enumerazione.  

 Un'associazione indica che il sistema sviluppato archivia collegamenti di un determinato tipo tra le istanze dei tipi associati. In genere, un'associazione non implica altro sull'implementazione dei collegamenti. Ad esempio, i collegamenti potrebbero essere puntatori, righe in una tabella, nomi soggetti a riferimenti incrociati in XML e così via.  

 Un'associazione è un metodo diagrammatico per mostrare un attributo o una coppia di attributi. Ad esempio, se una classe Restaurant è stata definita in modo da includere un attributo di tipo Menu, è possibile indicare la stessa definizione tracciando un'associazione tra Restaurant e Menu.  

 Per tracciare un'associazione, fare clic su **Association** della casella degli strumenti, scegliere il primo tipo, quindi il secondo. È possibile fare clic sullo stesso tipo due volte per indicare che le istanze possono essere collegate ad altre istanze dello stesso tipo.  

## <a name="properties"></a>Properties  
 Sono le proprietà di un'associazione in un diagramma classi UML.  

 Per visualizzare le proprietà di un'associazione, fare doppio clic sull'associazione e quindi fare clic su **proprietà**. Le proprietà verranno visualizzate nella finestra Proprietà.  

 Alcune delle proprietà sono visibili anche nel diagramma, come mostrato nella figura seguente.  

 ![Proprietà nelle associazioni](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Proprietà**|Descrizione|  
|------------------|-----------------|  
|**Nome (1)**|Identifica l'associazione. Viene visualizzata anche nel diagramma accanto al punto intermedio dell'associazione.|  
|**Nome completo**|Identifica in modo univoco l'associazione. Ha come prefisso il nome qualificato del pacchetto che contiene il primo ruolo dell'associazione.|  
|**Elementi di lavoro**|Numero di elementi di lavoro collegati a questa associazione. Per collegare gli elementi di lavoro, vedere [collegare elementi di modello ed elementi di lavoro](../modeling/link-model-elements-and-work-items.md).|  
|**Colore**|Colore del connettore. Diversamente dalle altre proprietà, è una proprietà di questa visualizzazione dell'associazione e non della relazione sottostante nel modello.|  
|**Primo ruolo**<br /><br /> **Secondo ruolo**|Ogni estremità dell'associazione è chiamata ruolo. Ogni ruolo descrive le proprietà dell'attributo equivalente nella classe all'estremità opposta dell'associazione.<br /><br /> Nel diagramma di esempio l'associazione tra Menu e Menu Item include ruoli chiamati Menu e Contents.<br /><br /> Contents è il nome di un attributo della classe Menu.|  

### <a name="properties-of-each-role"></a>Proprietà di ogni ruolo  
 Per visualizzare le proprietà di ogni ruolo, espandere la **primo ruolo** oppure **secondo ruolo** proprietà.  

|     **Proprietà**     |          **Default**          |                                                                                                                                                                                                                                                                                                                                        Descrizione                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nome del ruolo (2)**   | Nome del tipo in questo ruolo |                                                                                                                                                                                                                                                                                                       Nome del ruolo. Viene visualizzata all'estremità dell'associazione nel diagramma.                                                                                                                                                                                                                                                                                                        |
|   **Aggregazione**    |             Nessuna              |                                                                        **Nessuno** (4): rappresenta una relazione generale tra istanze delle classi.<br /><br /> **Composite** (5): l'oggetto in corrispondenza di questo ruolo contiene l'oggetto presso il ruolo opposto. È possibile usare la **composito** dello strumento per creare un'associazione con l'aggregazione Composite.<br /><br /> **Condiviso** (6) - oggetto in corrispondenza di questo ruolo contiene riferimenti all'oggetto in altro ruolo. È possibile usare la **aggregazione** dello strumento per creare un'associazione con l'aggregazione Shared.<br /><br /> L'interpretazione esatta è aperta alla convenzione locale.                                                                         |
|    **È derivato**    |             False             |                                                                                                                                                                                                                          Se true, l'oggetto a questa estremità del collegamento viene calcolato da altri attributi e associazioni. Ad esempio, MyWorkPlace viene calcolato da MyEmployer.WorkPlace. I dettagli devono essere digitati nella descrizione o in un commento allegato.                                                                                                                                                                                                                           |
| **Viene derivato Union** |             False             |                                                                                                                                                                                                                                                                                                             Se true, il ruolo è l'unione di un set di ruoli in tipi derivati.                                                                                                                                                                                                                                                                                                             |
|   **È esplorabile**   |             True              |                                                 L'associazione può essere letta in questa direzione. Data un'istanza del ruolo opposto, il software descritto può determinare in modo efficiente l'istanza associata in questo ruolo.<br /><br /> Se un ruolo è impostato su Is Navigable e l'altro no, viene visualizzata una freccia (7) sull'associazione nella direzione navigabile.<br /><br /> Per impostazione predefinita, lo strumento di associazione crea un'associazione leggibile in una sola direzione. Per convertirla in un'associazione bidirezionale, è possibile selezionare l'associazione, fare clic sul tag azione visualizzato e quindi fare clic su **Rendi bidirezionale**.                                                 |
|   **È di sola lettura**   |             False             |                                                                                                                                                                                                                                                                                   Se true, un'istanza dell'associazione non può essere modificata dopo che è stata creata. Il collegamento è sempre allo stesso oggetto.                                                                                                                                                                                                                                                                                    |
| **Molteplicità (3)** |               1               | **1** -questa estremità dell'associazione è sempre collegata a un oggetto. Nella figura ogni elemento Menu Item ha un elemento Menu.<br /><br /> **0..1** : questa estremità dell'associazione è collegata a un oggetto oppure non vi è alcun collegamento.<br /><br /> **\\** \* -ogni oggetto a altra estremità dell'associazione è collegato a una raccolta di oggetti a questa estremità e la raccolta può essere vuota.<br /><br /> **1..\\**  \* -ogni oggetto a altra estremità dell'associazione è collegato almeno un oggetto a questa estremità. Nella figura ogni elemento Menu ha almeno un elemento Menu Item.<br /><br /> *n* **..** *m* -ogni oggetto a altra estremità ha una raccolta di tra *n* e *m* i collegamenti agli oggetti a questa estremità. |
|    **È ordinato**    |             False             |                                                                                                                                                                                                                                                                                                  Se true, la raccolta restituita forma un elenco sequenziale. Per Multiplicity maggiore di 1.                                                                                                                                                                                                                                                                                                   |
|    **È univoco**     |             False             |                                                                                                                                                                                                                                                                                              Se true, non sono presenti valori duplicati nella raccolta restituita. Per Multiplicity maggiore di 1.                                                                                                                                                                                                                                                                                              |
|    **Visibilità**    |            Public             |                                                                                                                                                                                                                                 Public: visibile a livello globale.<br /><br /> Private: non visibile all'esterno del tipo proprietario.<br /><br /> Protected: visibile ai tipi derivati dal proprietario.<br /><br /> Package: visibile ad altri tipi all'interno dello stesso pacchetto.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Vedere anche  
 [Diagrammi delle classi UML: Riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagrammi delle classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)
