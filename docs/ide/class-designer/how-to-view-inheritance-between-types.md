---
title: Visualizzare l'ereditarietà tra tipi
description: Informazioni su come trovare la relazione di ereditarietà tra un tipo di base e i relativi tipi derivati in un diagramma classi in Progettazione classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.AssociationTypeNotFoundError
helpviewer_keywords:
- types [Visual Studio], inheritance
- types [Visual Studio], base
- types [Visual Studio], derived
ms.assetid: ea3f0ada-f53b-4fb1-9fb5-908286f5ec3e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ba469d7f4d9460b6c53ae37432d65a941e0d8fcb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078453"
---
# <a name="how-to-view-inheritance-between-types-in-class-designer"></a>Procedura: Visualizzare l'ereditarietà tra tipi in Progettazione classi

In **Progettazione classi** è possibile visualizzare la relazione di ereditarietà, se disponibile, tra un tipo di base e i relativi tipi derivati nel diagramma classi. Per creare una relazione di ereditarietà tra due tipi, se non ne esiste alcuna, vedere [Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md).

## <a name="to-find-the-base-type"></a>Per trovare il tipo di base

1. Nel diagramma classi selezionare il tipo per il quale si desidera visualizzare la classe o l'interfaccia base.

2. Scegliere **Mostra classe base** o **Mostra interfacce di base** dal menu **Diagramma classi**.

     La classe o l'interfaccia base del tipo risulterà selezionata nel diagramma. Le eventuali linee di ereditarietà nascoste saranno ora visibili tra le due forme.

È anche possibile fare clic con il pulsante destro del mouse sul tipo di cui si vuole visualizzare il tipo di base e scegliere **Mostra classe base** o **Mostra interfacce di base**.

## <a name="to-find-the-derived-types"></a>Per trovare i tipi derivati

1. Nel diagramma classi selezionare il tipo per il quale si desidera visualizzare le classi o le interfacce derivate.

2. Scegliere **Mostra classi derivate** o **Mostra interfacce derivate** dal menu **Diagramma classi**.

     Le classi o le interfacce derivate del tipo verranno visualizzate nel diagramma. Le eventuali linee di ereditarietà nascoste saranno ora visibili tra le forme.

È anche possibile fare clic con il pulsante destro del mouse sul tipo per il quale si vogliono visualizzare i tipi derivati e scegliere **Mostra classi derivate** o **Mostra interfacce derivate**.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare associazioni tra tipi](how-to-create-associations-between-types.md)
- [Visualizzazione di tipi e relazioni](designing-and-viewing-classes-and-types.md)
