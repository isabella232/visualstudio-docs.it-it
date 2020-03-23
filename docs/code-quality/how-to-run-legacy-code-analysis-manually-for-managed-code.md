---
title: "Procedura: eseguire manualmente l'analisi del codice legacy per il codice gestitoHow to: Run legacy code analysis manually for managed code"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432231"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Procedura: eseguire manualmente l'analisi del codice legacy per il codice gestitoHow to: Run legacy code analysis manually for managed code
Lo strumento di analisi del codice fornisce informazioni sui possibili difetti nel codice sorgente. È possibile eseguire automaticamente l'analisi del codice con ogni compilazione di un progetto di codice ed è anche possibile eseguire manualmente l'analisi del codice. Le regole controllate durante l'esecuzione dell'analisi del codice vengono specificate nella pagina Analisi codice delle pagine delle proprietà del progetto. Per ulteriori informazioni, vedere [Procedura: configurare l'analisi del codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Per eseguire manualmente l'analisi del codice

1. Se si utilizza Visual Studio 2019 versione 16.5 o successiva, eseguire il comando seguente al prompt dei comandi prima di avviare Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. In **Esplora soluzioni**fare clic sul progetto.

3. Scegliere **Esegui** analisi **codice in** *Nome progetto*dal menu Analizza .

