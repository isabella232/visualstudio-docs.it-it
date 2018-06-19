---
title: Sicurezza dei modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947521"
---
# <a name="security-of-text-templates"></a>Sicurezza dei modelli di testo
Modelli di testo sono i seguenti problemi di protezione:

-   Modelli di testo sono vulnerabili a inserimenti di codice arbitrario.

-   Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è protetto, è possibile eseguire un processore di direttiva dannoso.

## <a name="arbitrary-code"></a>Codice arbitrario
 Quando si scrive un modello, è possibile inserire qualsiasi codice all'interno di \<# # > tag. In questo modo il codice non autorizzato per l'esecuzione da all'interno di un modello di testo.

 Assicurarsi di ottenere modelli da origini attendibili. Assicurarsi di avvertire gli utenti finali dell'applicazione non eseguire modelli che non provengono da origini attendibili.

## <a name="malicious-directive-processor"></a>Processore di direttiva dannoso
 Il motore del modello di testo interagisce con un host di trasformazione e uno o più processori di direttive per trasformare il testo del modello in un file di output. Per ulteriori informazioni, vedere [il processo di trasformazione di modello di testo](../modeling/the-text-template-transformation-process.md).

 Se il meccanismo utilizzato dall'host per trovare un processore di direttiva non è protetto, viene eseguito il rischio di eseguire un processore di direttiva dannoso. Il processore di direttiva dannoso potrebbe fornire codice che viene eseguito in `FullTrust` modalità quando viene eseguito il modello. Se si crea un host di trasformazione del modello testo personalizzato, è necessario utilizzare un meccanismo protetto, ad esempio il Registro di sistema per il motore per individuare i processori di direttiva.