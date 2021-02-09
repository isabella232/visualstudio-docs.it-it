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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924502"
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
