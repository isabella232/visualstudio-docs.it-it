---
title: Quando i payload dei pacchetti cambiano dopo un rilascio
description: Quando si crea un layout, scoprire come determinare se i payload dei pacchetti sono cambiati dopo il rilascio di una versione.
ms.date: 05/22/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dec1478314e752ddace8fae822747e7c8e328b70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114584"
---
# <a name="package-payload-changes"></a>Modifiche al payload del pacchetto

Alcuni payload di pacchetti possono cambiare dopo il rilascio di una versione. Quando qualcuno crea un layout, questo comportamento potrebbe causare un contenuto diverso del layout, a seconda di quando è stato creato un layout.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Verificare che un layout includa le modifiche al payload del pacchetto

Ecco come determinare se il layout creato in precedenza abbia acquisito i payload di pacchetti modificati dopo il rilascio di una versione:

1. Aprire il log di installazione. Il log si trova in genere in `%TEMP%\dd_setup_[date].log`, dove `[date]` indica la data di inizio dell'operazione di layout nel formato `yyyyMMddHHmmss`.

2. Cercare una riga nel log strutturata come il testo seguente:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Cercare quindi righe successive nel log che indichino che il download ha avuto esito positivo per [path]. Potrebbero essere simili al testo seguente:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Vedere anche

* [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
