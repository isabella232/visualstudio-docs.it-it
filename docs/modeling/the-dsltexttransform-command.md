---
title: Comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89d83da450014ebf29e2882438d27f9284c9bbbb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939034"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
DslTextTransform.cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation.cmd per una compilazione notturna di automatizzare il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] progetti. Per altre informazioni, vedere [generazione di file con l'utilità di TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd si trova nella directory seguente:

 **\<Percorso di installazione di Visual Studio SDK > \visualstudiointegration\tools\bin.**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform.cmd:

- La directory di output del progetto di modello di dominio.

- La directory di output del progetto di definizione della finestra di progettazione.

- Il percorso del file di modello di testo.

  DslTextTransform.cmd elabora il file di modello di testo specificato usando i processori di direttive predefinito e gli assembly. Se si creano i processori di direttiva personalizzati, è possibile creare il proprio file batch che chiama TextTransform.exe. In questo file batch, è possibile specificare gli assembly e i processori di direttiva personalizzati associati.