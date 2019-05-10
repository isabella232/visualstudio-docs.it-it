---
title: Estendere i diagrammi delle dipendenze
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c164174b88ca9fdd815668084c1447e20de072c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476560"
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi delle dipendenze

È possibile scrivere codice per creare e aggiornare i diagrammi delle dipendenze e per convalidare la struttura del codice programma in base ai diagrammi delle dipendenze in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

## <a name="requirements"></a>Requisiti

È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Modeling SDK per Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È necessario disporre di un'edizione di Visual Studio installata nel computer in cui si desidera eseguire le estensioni del livello appropriata. Per informazioni su quali edizioni di Visual Studio che supportano i diagrammi delle dipendenze, vedere [supporto di edizione per un'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Vedere anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
