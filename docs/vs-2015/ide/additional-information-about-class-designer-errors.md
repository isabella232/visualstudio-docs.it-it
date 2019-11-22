---
title: Informazioni aggiuntive sugli errori di Progettazione classi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10eb94783abbd63ca152fbf73a544665199ba137
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300290"
---
# <a name="additional-information-about-class-designer-errors"></a>Informazioni aggiuntive sugli errori di Progettazione classi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Progettazione classi non tiene traccia del percorso dei file di origine. Di conseguenza, se si modifica la struttura del progetto o si spostano i file di origine in un progetto, Progettazione classi può perdere traccia del tipo, soprattutto del tipo di origine di un typedef, delle classi di base o dei tipi di associazione. Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. In tal caso, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo nuovamente.

 Nelle risorse seguenti è possibile trovare assistenza per altri errori e avvisi:

 [L'utilizzo di C++ codice visuale (Progettazione classi)](../ide/working-with-visual-cpp-code-class-designer.md) include informazioni sulla risoluzione C++ dei problemi di visualizzazione in un diagramma classi.

 [Forum su Progettazione classi di Visual Studio](https://go.microsoft.com/fwlink/?LinkId=160754) Forum dedicato a domande su Progettazione classi.

## <a name="see-also"></a>Vedere anche
 [Progettazione e visualizzazione di classi e tipi](../ide/designing-and-viewing-classes-and-types.md)
