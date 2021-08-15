---
title: Sintassi del percorso di dominio
description: Informazioni sulla sintassi del percorso di dominio e su come le definizioni DSL usano una sintassi simile a XPath per individuare elementi specifici in un modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: a5e3a80c09456cf50a021410a2df6ecc1ae65cc97e9897eb1682c054840df9e7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316812"
---
# <a name="domain-path-syntax"></a>Sintassi del percorso di dominio
Le definizioni DSL usano una sintassi di tipo XPath per individuare elementi specifici in un modello.

 Normalmente, non è necessario usare questa sintassi direttamente. Se presente nella finestra Dettagli DSL o Proprietà, è possibile fare clic sulla freccia rivolta verso il basso e usare l'editor dei percorsi. Tuttavia, il percorso viene visualizzato in questo formato nel campo dopo avere usato l'editor.

 Un percorso di dominio usa il formato seguente:

 *RelationshipName.PropertyName/!Role*

 ![Relazione di riferimento CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 La sintassi attraversa l'albero del modello. Ad esempio, la relazione di dominio **CommentReferencesSubjects nella** figura precedente ha un **ruolo Soggetti.** Segmento di percorso **/! Subjectt** specifica che il percorso termina sugli elementi a cui si accede tramite il **ruolo Soggetti.**

 Ogni segmento inizia con il nome di una relazione di dominio. Se l'attraversamento è da un elemento a una relazione, il segmento di percorso viene visualizzato *come Relationship.PropertyName*. Se l'hop è da un collegamento a un elemento, il segmento di percorso viene visualizzato *come Relazione/! RoleName*.

 Le barre separano la sintassi di un percorso. Ogni segmento di percorso è un hop da un elemento a un collegamento (istanza di una relazione) o da un collegamento a un elemento. I segmenti di percorso vengono visualizzati spesso in coppie. Un segmento di percorso rappresenta un hop da un elemento a un collegamento e il segmento successivo rappresenta un hop dal collegamento all'elemento all'altra estremità. Un collegamento può anche essere l'origine o la destinazione di una relazione stessa.

 Il nome usato per l'hop da un elemento a un collegamento corrisponde al valore dell'oggetto `Property Name` del ruolo. Il nome usato per l'hop da un collegamento a un elemento corrisponde al nome del ruolo di destinazione.

## <a name="see-also"></a>Vedi anche

- [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)
