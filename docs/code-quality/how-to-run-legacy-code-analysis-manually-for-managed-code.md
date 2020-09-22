---
title: Eseguire manualmente l'analisi del codice legacy (.NET)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ca865b33d59f87453cafc337e1595c9d772b17a2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808613"
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
