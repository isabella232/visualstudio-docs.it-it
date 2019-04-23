---
title: 'Procedura: Installare un visualizzatore | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5b27d52c1f390e6c9f60ef10a91d9a93f903f5c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104486"
---
# <a name="how-to-install-a-visualizer"></a>Procedura: Installare un visualizzatore
Dopo avere creato un visualizzatore, è necessario installarlo in modo da renderlo disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per installare un visualizzatore è sufficiente seguire una semplice procedura.

> [!NOTE]
>  Nelle App UWP, solo il testo standard, sono supportati i visualizzatori HTML, XML e JSON. Non sono supportati i visualizzatori personalizzati (creati dall'utente).

### <a name="to-install-a-visualizer"></a>Per installare un visualizzatore

1. Individuare la DLL contenente il visualizzatore compilato.

2. Copiare la DLL in uno dei seguenti percorsi:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Se si desidera usare un visualizzatore gestito per il debug remoto, copiare la DLL nello stesso percorso nel computer remoto.

4. Riavviare la sessione di debug.

## <a name="see-also"></a>Vedere anche
- [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)
- [Procedura: Scrivere un visualizzatore](/visualstudio/debugger/create-custom-visualizers-of-data)