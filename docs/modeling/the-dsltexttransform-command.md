---
title: Comando DslTextTransform
description: Si apprenderà che DslTextTransform. cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f87f735f5ad6864082046327bc852d5d43fdb6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362717"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform. cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation. cmd per automatizzare una compilazione notturna dei [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per altre informazioni, vedere [generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd si trova nella directory seguente:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform. cmd:

- Directory di output del progetto di modello di dominio.

- Directory di output del progetto di definizione della finestra di progettazione.

- Percorso del file di modello di testo.

  DslTextTransform. cmd elabora il file del modello di testo specificato utilizzando i processori di direttiva e gli assembly predefiniti. Se si creano processori di direttive personalizzati, è possibile creare un file batch personalizzato che chiama TextTransform.exe. In questo file batch è possibile specificare gli assembly e i processori di direttiva personalizzati associati.
