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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669731"
---
# <a name="domain-path-syntax"></a>Sintassi del percorso di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le definizioni DSL usano una sintassi di tipo XPath per individuare elementi specifici in un modello.

 Normalmente, non è necessario usare questa sintassi direttamente. Se presente nella finestra Dettagli DSL o Proprietà, è possibile fare clic sulla freccia rivolta verso il basso e usare l'editor dei percorsi. Tuttavia, il percorso viene visualizzato in questo formato nel campo dopo avere usato l'editor.

 Un percorso di dominio usa il formato seguente:

 *RelationshipName. PropertyName/! Ruolo*

 ![Relazione di riferimento CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")

 La sintassi attraversa l'albero del modello. La relazione di dominio **CommentReferencesSubjects** nell'illustrazione precedente, ad esempio, ha un ruolo **Subjects** . Segmento di percorso **/! Subjectt** specifica che il percorso termina con gli elementi a cui si accede tramite il ruolo **Subjects** .

 Ogni segmento inizia con il nome di una relazione di dominio. Se l'attraversamento è da un elemento a una relazione, il segmento di percorso viene visualizzato come *Relationship. PropertyName*. Se l'hop è da un collegamento a un elemento, il segmento di percorso viene visualizzato come *Relationship/! RoleName*.

 Le barre separano la sintassi di un percorso. Ogni segmento di percorso è un hop da un elemento a un collegamento (istanza di una relazione) o da un collegamento a un elemento. I segmenti di percorso vengono visualizzati spesso in coppie. Un segmento di percorso rappresenta un hop da un elemento a un collegamento e il segmento successivo rappresenta un hop dal collegamento all'elemento all'altra estremità. Un collegamento può anche essere l'origine o la destinazione di una relazione stessa.

 Il nome usato per l'hop da un elemento a un collegamento corrisponde al valore dell'oggetto `Property Name` del ruolo. Il nome usato per l'hop da un collegamento a un elemento corrisponde al nome del ruolo di destinazione.

## <a name="see-also"></a>Vedere anche
 [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)
