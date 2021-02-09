---
title: Sicurezza dei modelli di testo
description: Informazioni sui modelli di sicurezza e di testo, inclusi argomenti come codice arbitrario e processori di direttive dannose.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11352eb33070d3401516948cc01c4b9bd7ab4f95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893321"
---
# <a name="security-of-text-templates"></a>Sicurezza dei modelli di testo
I modelli di testo presentano i seguenti problemi di sicurezza:

- I modelli di testo sono vulnerabili agli inserimenti di codice arbitrari.

- Se il meccanismo usato dall'host per trovare un processore di direttiva non è sicuro, è possibile eseguire un processore di direttive dannose.

## <a name="arbitrary-code"></a>Codice arbitrario
 Quando si scrive un modello, è possibile inserire qualsiasi codice all'interno dei \<# #> tag. Questo consente l'esecuzione di codice arbitrario dall'interno di un modello di testo.

 Assicurarsi di ottenere modelli da origini attendibili. Assicurarsi di avvisare gli utenti finali dell'applicazione in modo che non eseguano modelli che non provengono da origini attendibili.

## <a name="malicious-directive-processor"></a>Processore di direttiva dannoso
 Il motore del modello di testo interagisce con un host di trasformazione e uno o più processori di direttiva per trasformare il testo del modello in un file di output. Per ulteriori informazioni, vedere [il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md).

 Se il meccanismo usato dall'host per trovare un processore di direttiva non è sicuro, viene eseguito il rischio di eseguire un processore di direttive dannose. Il processore di direttiva dannosa potrebbe fornire codice eseguito in `FullTrust` modalità quando il modello viene eseguito. Se si crea un host di trasformazione del modello di testo personalizzato, è necessario utilizzare un meccanismo protetto, ad esempio il registro di sistema, per individuare i processori di direttiva da parte del motore.
