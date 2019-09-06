---
title: Unit test di un'app in contenitori
author: ghogen
description: Eseguire unit test con ogni compilazione per un progetto Docker in Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2019
ms.locfileid: "70311989"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Procedura: Eseguire unit test per un'app in contenitori

È possibile eseguire unit test con ogni compilazione del progetto in contenitori modificando il Dockerfile.

## <a name="prerequisites"></a>Prerequisiti

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Installare [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Unit test configurati per l'esecuzione con [test DotNet](/dotnet/core/tools/dotnet-test)
- Installare l' [estensione della finestra contenitori](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Aggiungere unit test a Dockerfile

Visual Studio esegue alcune ottimizzazioni delle prestazioni speciali prima di modificare il Dockerfile. Quando si compila la configurazione di **debug** , Visual Studio compila i progetti nel computer locale e copia i risultati nel contenitore. Quindi, solo la prima fase del Dockerfile multifase viene eseguita come specificato in Dockerfile. Per altre informazioni, vedere [processo di compilazione degli strumenti contenitore per Visual Studio](container-build.md).

Per aggiungere unit test a un Dockerfile multifase, aggiungere una `unit-test` fase al Dockerfile tra le `build` fasi e `publish` .

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

Visual Studio esegue solo la prima fase nella configurazione di **debug** , quindi `unit-test` la fase viene eseguita solo nella configurazione di **rilascio** . Tuttavia, anche nella configurazione di **versione** , i risultati dei log non verranno inclusi nell'immagine finale, perché l'immagine finale è compilata dalla `base` fase `unit-test` , non dalla fase. Per eseguire i test e produrre un'immagine in cui è possibile visualizzare i log, usare il comando seguente:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Passaggi successivi

È quindi possibile usare la [finestra contenitori](view-and-diagnose-containers.md) , se è stata installata l'estensione, per visualizzare i log di test.  

Per visualizzare i log di test, usare **CTRL**+**Q** e cercare i **contenitori** per aprire la finestra **contenitori** . Nella finestra **contenitori** trovare il contenitore, aprire la scheda **file** , cercare il file dei risultati del test (con estensione TRX) nel file System del contenitore e aprirlo per visualizzare i risultati in Visual Studio.

