---
title: Sicurezza dei modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9906f3b8af624e1761b73c3338bad98b263aa9e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957182"
---
# <a name="security-of-text-templates"></a>Sicurezza dei modelli di testo
I modelli di testo presentano i problemi di sicurezza seguenti:

-   Modelli di testo sono vulnerabili a operazioni di inserimento di codice arbitrario.

-   Se il meccanismo usato dall'host per trovare un processore di direttiva non è protetto, è possibile eseguire un processore di direttiva dannoso.

## <a name="arbitrary-code"></a>Esecuzione di codice arbitrario
 Quando si scrive un modello, è possibile inserire il codice all'interno di \<# # > tag. In questo modo arbitraria di codice essere eseguito in un modello di testo.

 Assicurarsi di ottenere modelli da fonti attendibili. Assicurarsi che avvisare gli utenti finali dell'applicazione non vengano eseguite modelli che non provengono da origini attendibili.

## <a name="malicious-directive-processor"></a>Processore di direttiva dannosi
 Il motore del modello testo interagisce con un host di trasformazione e uno o più processori di direttive per trasformare il testo del modello in un file di output. Per altre informazioni, vedere [il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md).

 Se il meccanismo usato dall'host per trovare un processore di direttiva non è protetto, viene eseguito il rischio di eseguire un processore di direttiva dannoso. Il processore di direttiva dannoso potrebbe fornire codice che viene eseguito in `FullTrust` modalità quando si esegue il modello. Se si crea un host di trasformazione del modello testo personalizzato, è necessario usare un meccanismo protetto, ad esempio il Registro di sistema per il motore individuare i processori di direttiva.