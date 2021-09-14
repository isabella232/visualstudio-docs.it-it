---
title: Sicurezza dei modelli di testo
description: Informazioni sui modelli di sicurezza e di testo, inclusi argomenti come codice arbitrario e processori di direttive dannosi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 376abb9674519cc87afdfd9af81bea4a6d495903
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637467"
---
# <a name="security-of-text-templates"></a>Sicurezza dei modelli di testo
I modelli di testo hanno i problemi di sicurezza seguenti:

- I modelli di testo sono vulnerabili agli inserimenti arbitrari di codice.

- Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è sicuro, è possibile eseguire un processore di direttiva dannoso.

## <a name="arbitrary-code"></a>Codice arbitrario
 Quando si scrive un modello, è possibile inserire qualsiasi codice all'interno dei \<# #> tag. Ciò consente l'esecuzione di codice arbitrario dall'interno di un modello di testo.

 Assicurarsi di ottenere modelli da origini attendibili. Assicurarsi di avvisare gli utenti finali dell'applicazione di non eseguire modelli che non provengono da origini attendibili.

## <a name="malicious-directive-processor"></a>Processore di direttiva dannoso
 Il motore del modello di testo interagisce con un host di trasformazione e con uno o più processori di direttiva per trasformare il testo del modello in un file di output. Per altre informazioni, vedere [Processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md).

 Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è sicuro, corre il rischio di eseguire un processore di direttiva dannoso. Il processore di direttiva dannoso potrebbe fornire codice che viene eseguito in `FullTrust` modalità quando viene eseguito il modello. Se si crea un host di trasformazione del modello di testo personalizzato, è necessario usare un meccanismo sicuro, ad esempio il Registro di sistema, per il motore per individuare i processori di direttiva.
