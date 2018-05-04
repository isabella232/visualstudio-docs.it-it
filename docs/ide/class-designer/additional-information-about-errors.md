---
title: Errori di Progettazione classi
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0af8686af556ca24cdbc9e0a51206f4f0728206
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="additional-information-about-class-designer-errors"></a>Informazioni aggiuntive sugli errori di Progettazione classi

**Progettazione classi** non tiene traccia del percorso dei file di origine. Di conseguenza, se si modifica la struttura del progetto o si spostano i file di origine in un progetto, **Progettazione classi** può perdere traccia del tipo (soprattutto del tipo di origine di un typedef, delle classi di base o dei tipi di associazione). Si potrebbe ricevere un errore, ad esempio **Progettazione classi: impossibile visualizzare il tipo**. In tal caso, trascinare di nuovo il codice sorgente modificato o riposizionato nel diagramma classi per visualizzarlo nuovamente.

## <a name="resources"></a>Risorse

Nelle risorse seguenti è possibile trovare assistenza per altri errori e avvisi:

- [Utilizzo di codice Visual C++](working-with-visual-cpp-code.md) include informazioni sulla risoluzione dei problemi relativi alla visualizzazione di C++ in un diagramma classi.
- Il [forum su Progettazione classi di Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) è un forum dedicato a domande su **Progettazione classi**.

## <a name="see-also"></a>Vedere anche

- [Progettazione e visualizzazione di classi e tipi](designing-and-viewing-classes-and-types.md)
