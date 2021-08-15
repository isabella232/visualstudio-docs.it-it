---
title: Comando DslTextTransform
description: Si apprenderà che DslTextTransform.cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 1c2bb7a6d4ce0304fbf0dcbf6c56778eaa189b3cd42d20f17876ae2770f1230d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316630"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation.cmd per automatizzare una compilazione notturna dei [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per altre informazioni, vedere [Generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd si trova nella directory seguente:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:

- Directory di output del progetto di modello di dominio.

- Directory di output del progetto di definizione della finestra di progettazione.

- Percorso del file modello di testo.

  DslTextTransform.cmd elabora il file del modello di testo specificato usando i processori di direttiva e gli assembly predefiniti. Se si creano processori di direttiva personalizzati, è possibile creare un file batch personalizzato che chiama TextTransform.exe. In questo file batch è possibile specificare gli assembly e i processori di direttiva personalizzati associati.
