---
title: Quando i payload dei pacchetti cambiano dopo un rilascio
description: Quando si crea un layout, scoprire come determinare se i payload dei pacchetti sono cambiati dopo il rilascio di una versione.
ms.date: 05/22/2019
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 22201f48f05e2ba6a40ea538ed9795b04fda7e54f755cb241f8570520a4b4068
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386459"
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

## <a name="see-also"></a>Vedi anche

* [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
