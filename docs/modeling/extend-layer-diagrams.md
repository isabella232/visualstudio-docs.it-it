---
title: Estendere i diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 305c562c7600dc6955ce0307db92f4e257fc1c21
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302945"
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi delle dipendenze

È possibile scrivere codice per creare e aggiornare diagrammi di dipendenza e per convalidare la struttura del codice del programma rispetto ai diagrammi di dipendenza in Visual Studio.You can write code to create and update dependency diagrams and to validate the structure of your program code against dependency diagrams in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

## <a name="requirements"></a>Requisiti

È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- SDK di modellazione per Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È necessario disporre di un'edizione appropriata di Visual Studio installata nel computer in cui si desidera eseguire le estensioni del livello. Per sapere quali edizioni di Visual Studio supportano i diagrammi di dipendenza, vedere [Supporto dell'edizione per gli strumenti di architettura e modellazione.](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="see-also"></a>Vedere anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
