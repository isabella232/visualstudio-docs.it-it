---
title: Estendere i diagrammi delle dipendenze
description: Informazioni su come scrivere codice per creare e aggiornare i diagrammi delle dipendenze e su come convalidare la struttura del codice del programma in base ai diagrammi di dipendenza in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10e0e07b6a8ee4245e19628e03bfdf484f94d34c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935144"
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi delle dipendenze

È possibile scrivere codice per creare e aggiornare i diagrammi delle dipendenze e per convalidare la struttura del codice del programma in base ai diagrammi di dipendenza in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.

## <a name="requirements"></a>Requisiti

È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:

- Visual Studio

- [SDK di Visual Studio](../extensibility/visual-studio-sdk.md)

- SDK di modellazione per Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È necessario che nel computer in cui si desidera eseguire le estensioni del livello sia installata un'edizione appropriata di Visual Studio. Per individuare le edizioni di Visual Studio che supportano i diagrammi di dipendenza, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Vedi anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
