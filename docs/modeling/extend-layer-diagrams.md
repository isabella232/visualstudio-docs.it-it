---
title: Estendere i diagrammi delle dipendenze
description: Informazioni su come scrivere codice per creare e aggiornare diagrammi delle dipendenze e come convalidare la struttura del codice del programma rispetto ai diagrammi di dipendenza in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4b51d2754ec3c48c9ca2f7a86640959221ff2a28
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040346"
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi delle dipendenze

È possibile scrivere codice per creare e aggiornare i diagrammi delle dipendenze e per convalidare la struttura del codice del programma rispetto ai diagrammi delle dipendenze in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

## <a name="requirements"></a>Requisiti

È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

- Visual Studio

- [Visual Studio Sdk](../extensibility/visual-studio-sdk.md)

- SDK di modellazione per Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È necessario avere un'edizione appropriata di Visual Studio installato nel computer in cui si vogliono eseguire le estensioni del livello. Per informazioni sulle edizioni di Visual Studio diagrammi delle dipendenze, vedere Supporto dell'edizione per gli strumenti di architettura [e modellazione](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="see-also"></a>Vedi anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
