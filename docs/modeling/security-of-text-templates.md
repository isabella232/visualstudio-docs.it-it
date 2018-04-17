---
title: Sicurezza dei modelli di testo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4acbe40d7229551e32f60d1503864b21840655be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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