---
title: Comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114910"
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
