---
title: Come eseguire manualmente l'analisi del codice legacy per il codice gestito
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 38c3de83dc0df39314ad236f647c69bbe614b75d
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371820"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Procedura: eseguire manualmente l'analisi del codice legacy per il codice gestito
Lo strumento di analisi del codice fornisce informazioni sul possibile difetto nel codice sorgente. È possibile eseguire l'analisi del codice automaticamente con ogni compilazione di un progetto di codice ed è anche possibile eseguire manualmente l'analisi del codice. Le regole controllate quando viene eseguita l'analisi del codice vengono specificate nella pagina analisi codice delle pagine delle proprietà del progetto. Per altre informazioni, vedere [procedura: configurare l'analisi del codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Per eseguire manualmente l'analisi del codice

1. Se si utilizza Visual Studio 2019 versione 16,5 o successiva, eseguire il comando seguente al prompt dei comandi prima di avviare Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. In **Esplora soluzioni**fare clic sul progetto.

3. Nel menu **analizza** fare clic su **Esegui analisi del codice sul** *nome del progetto*.

