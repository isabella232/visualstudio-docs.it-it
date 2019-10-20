---
title: Comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605936"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform. cmd è uno script che chiama TextTransform. exe e lo esegue con le opzioni comuni. È possibile usare DslTextTransformation. cmd per automatizzare una compilazione notturna dei progetti [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Per altre informazioni, vedere [generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd si trova nella directory seguente:

 **Percorso di installazione di \<Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform. cmd:

- Directory di output del progetto di modello di dominio.

- Directory di output del progetto di definizione della finestra di progettazione.

- Percorso del file di modello di testo.

  DslTextTransform. cmd elabora il file del modello di testo specificato utilizzando i processori di direttiva e gli assembly predefiniti. Se si creano processori di direttive personalizzati, è possibile creare un file batch personalizzato che chiama TextTransform. exe. In questo file batch è possibile specificare gli assembly e i processori di direttiva personalizzati associati.