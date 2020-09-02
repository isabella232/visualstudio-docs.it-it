---
title: Errori di Progettazione classi
ms.date: 11/04/2016
ms.topic: troubleshooting
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
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8b2c013a3e685a6071f4a12d63e3ca475051a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596515"
---
# <a name="class-designer-errors"></a>Errori di Progettazione classi

**Progettazione classi** non tiene traccia del percorso dei file di origine, quindi, se si modifica la struttura del progetto o si spostano i file di origine del progetto, **Progettazione classi** può perdere traccia del tipo. Accade spesso, ad esempio, che si modifichi il tipo di origine di un typedef, delle classi di base e dei tipi di associazione. Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. Per risolvere l'errore, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo.

## <a name="resources"></a>Risorse

Nelle risorse seguenti è possibile trovare assistenza per altri errori e avvisi:

- [Usare il codice Visual C++](working-with-visual-cpp-code.md) include informazioni sulla risoluzione dei problemi relativi alla visualizzazione di C++ in un diagramma classi.
- Il [forum su Progettazione classi di Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) è un forum dedicato a domande su **Progettazione classi**.

## <a name="see-also"></a>Vedere anche

- [Progettazione e visualizzazione di classi e tipi](designing-and-viewing-classes-and-types.md)
