---
title: Eseguire manualmente l'analisi del codice legacy (.NET)
description: Informazioni su come rilevare possibili difetti nel codice sorgente. Vedere come eseguire manualmente l'analisi del codice legacy sul codice gestito in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 7471cc1d5b7a3aaa90ae2329d080e4c9e68a2db9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122044995"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Procedura: Eseguire manualmente l'analisi del codice legacy per il codice gestito

Lo strumento di analisi del codice fornisce informazioni sui possibili difetti nel codice sorgente. È possibile eseguire automaticamente l'analisi del codice a ogni compilazione di un progetto di codice ed è anche possibile eseguire manualmente l'analisi del codice. Le regole controllate quando viene eseguita l'analisi del codice vengono specificate nella Code Analysis delle pagine delle proprietà del progetto. Per altre informazioni, vedere [Procedura: Configurare la Code Analysis per un'istanza di codice Project](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Per eseguire manualmente l'analisi del codice

1. Se si è in Visual Studio 2019 versione 16.5 o successiva, eseguire il comando seguente al prompt dei comandi prima di avviare Visual Studio:

```
setx EnableLegacyCodeAnalysis true
```

2. Nella **Esplora soluzioni** fare clic sul progetto.

3. Nel menu **Analizza** fare clic su **Esegui Code Analysis in Project** *nome*.
