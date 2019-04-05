---
title: Sintassi del percorso di dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2c115e8fff6cddbc1b08c697b72c7bda3a970ed4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970045"
---
# <a name="domain-path-syntax"></a>Sintassi del percorso di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le definizioni DSL usano una sintassi di tipo XPath per individuare elementi specifici in un modello.  
  
 Normalmente, non è necessario usare questa sintassi direttamente. Se presente nella finestra Dettagli DSL o Proprietà, è possibile fare clic sulla freccia rivolta verso il basso e usare l'editor dei percorsi. Tuttavia, il percorso viene visualizzato in questo formato nel campo dopo avere usato l'editor.  
  
 Un percorso di dominio usa il formato seguente:  
  
 *RelationshipName.PropertyName/!Role*  
  
 ![Relazione di riferimento CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")  
  
 La sintassi attraversa l'albero del modello. Ad esempio, la relazione di dominio **CommentReferencesSubjects** nella figura sopra riportata ha un **soggetti** ruolo. Il segmento di percorso **/! Subjectt** specifica che il percorso termina con gli elementi accessibili tramite il **soggetti** ruolo.  
  
 Ogni segmento inizia con il nome di una relazione di dominio. Se l'attraversamento è da un elemento a una relazione, il segmento di percorso viene visualizzato come *PropertyName*. Se l'hop è da un collegamento a un elemento, il segmento di percorso viene visualizzato come *Relationship /! RoleName*.  
  
 Le barre separano la sintassi di un percorso. Ogni segmento di percorso è un hop da un elemento a un collegamento (istanza di una relazione) o da un collegamento a un elemento. I segmenti di percorso vengono visualizzati spesso in coppie. Un segmento di percorso rappresenta un hop da un elemento a un collegamento e il segmento successivo rappresenta un hop dal collegamento all'elemento all'altra estremità. Un collegamento può anche essere l'origine o la destinazione di una relazione stessa.  
  
 Il nome usato per l'hop da un elemento a un collegamento corrisponde al valore dell'oggetto `Property Name` del ruolo. Il nome usato per l'hop da un collegamento a un elemento corrisponde al nome del ruolo di destinazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)
