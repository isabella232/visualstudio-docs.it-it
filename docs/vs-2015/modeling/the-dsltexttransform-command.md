---
title: Comando DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658458"
---
# <a name="the-dsltexttransform-command"></a>Comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd è uno script che chiama TextTransform.exe e lo esegue con opzioni comuni. È possibile usare DslTextTransformation. cmd per automatizzare una compilazione notturna dei [!INCLUDE[dsl](../includes/dsl-md.md)] progetti. Per altre informazioni, vedere [generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd si trova nella directory seguente:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 È possibile specificare gli argomenti seguenti come input per DslTextTransform. cmd:

- Directory di output del progetto di modello di dominio.

- Directory di output del progetto di definizione della finestra di progettazione.

- Percorso del file di modello di testo.

  DslTextTransform. cmd elabora il file del modello di testo specificato utilizzando i processori di direttiva e gli assembly predefiniti. Se si creano processori di direttive personalizzati, è possibile creare un file batch personalizzato che chiama TextTransform.exe. In questo file batch è possibile specificare gli assembly e i processori di direttiva personalizzati associati.
